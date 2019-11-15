.. asteval documentation master file,

ASTEVAL: Minimal Python AST Evaluator
================================================

.. _numpy: http://docs.scipy.org/doc/numpy

The asteval package evaluates mathematical expressions and statements,
providing a safer alternative to Python's builtin :py:func:`eval` and a
richer, easier to use alternative to :py:func:`ast.literal_eval`.  It does
this by building an embedded interpreter for a subset of the Python
language using Python's :py:mod:`ast` module.  The emphasis here and main
area of application is the evaluation of mathematical expressions. Because
of this, mathematical functions from Python's :py:mod:`math` module are
available, and a large number of functions from `numpy`_ will be available
if `numpy`_ is installed on your system.

While the emphasis is on basic mathematical expressions, many features of the
Python language are supported by default.  These features include array
slicing and subscripting, if-then-else conditionals, while loops, for loops,
try-except blocks, list comprehension, and user-defined functions.  All
objects in the asteval interpreter are truly python objects, and all basic
built-in data structures (strings, dictionaries, tuple, lists, numpy arrays)
are supported.

However, Asteval is by no means an attempt to reproduce Python with its own
:py:mod:`ast` module.  There are important differences and missing features
compared to Python.  Many of these absences are intentionally trying to make a
safer version of :py:func:`eval`, while some are simply due to the reduced
requirements for a small embedded min-language. Some of the main differences
and absences include:

 1. Variable and function symbol names are held in a simple symbol
    table - a single dictionary - giving a flat namespace.
 2. creating classes is not allowed.
 3. importing modules is not allowed.
 4. function decorators, generators, yield, and lambda are not supported.
 5. Many builtins (:py:func:`eval`, :py:func:`execfile`,
    :py:func:`getattr`, :py:func:`hasattr`, :py:func:`setattr`, and
    :py:func:`delattr`) are not allowed.
 6. Accessing several private object attributes that can provide access to
    the python interpreter are not allowed.

The effect to make the asteval mini-language look and act very much like
miniature version of Python itself focused on mathematical calculations, and
with noticeable limitations.


Because asteval is suitable for evaluating user-supplied input strings, safety
against malicious or incompetent user input is an important concern.  Asteval
tries as hard as possible to prevent user-supplied input from crashing the
Python interpreter or from returning exploitable parts of the Python
interpreter.  In this sense asteval is certainly safer than using
:py:func:`eval`.  However, asteval is an open source project written by
volunteers, and we cannot guarantee that it is completely safe against
malicious attacks.

.. toctree::
   :maxdepth: 2

   installation
   motivation
   basics
   api
