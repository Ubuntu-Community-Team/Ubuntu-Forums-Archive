---
title: "Scipy ODR test failed"
date: 2010-09-24
forum: General Help
---

### Post by icpup on 2010-09-24
I have Lucid 10.04 x86_64 and python 2.6.5. After install numpy1.3.0 and scipy 0.7.0 from repository, I run a test on numpy and scipy. The numpy test was OK, but the scipy test was failed on ODR testing. The screen print-out was shown below:
>>> scipy.test()
Running unit tests for scipy
NumPy version 1.3.0
NumPy is installed in /usr/lib/python2.6/dist-packages/numpy
SciPy version 0.7.0
SciPy is installed in /usr/lib/python2.6/dist-packages/scipy
Python version 2.6.5 (r265:79063, Apr 16 2010, 13:57:41) [GCC 4.4.3]
nose version 0.11.4
...
.........warning: specified build_dir '_bad_path_' does not exist or is not writable. Trying default locations
...warning: specified build_dir '..' does not exist or is not writable. Trying default locations
..warning: specified build_dir '_bad_path_' does not exist or is not writable. Trying default locations
...warning: specified build_dir '..' does not exist or is not writable. Trying default locations
............................................................................................................................
======================================================================
ERROR: test_implicit (test_odr.TestODR)
----------------------------------------------------------------------
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/scipy/odr/tests/test_odr.py", line 88, in test_implicit
    out = implicit_odr.run()
  File "/usr/lib/python2.6/dist-packages/scipy/odr/odrpack.py", line 1055, in run
    self.output = Output(apply(odr, args, kwds))
TypeError: y must be a sequence or integer (if model is implicit)

----------------------------------------------------------------------
Ran 2587 tests in 27.774s

FAILED (KNOWNFAIL=3, SKIP=13, errors=1)
<nose.result.TextTestResult run=2587 errors=1 failures=0>
>>> 

Is scipy broken in this build?

---

