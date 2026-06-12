---
title: "stability test for GPU?"
date: 2012-04-26
forum: General Help
---

### Post by P3t3r on 2012-04-26
Are there any tools to test GPU stability of an AMD GPU under Ubuntu? Usually these are used to test whether a certain overclock is stable. For one of my cards, I think it's unstable even at stock speed. But furmark, occt and all the similar tests are windows-only. How should I test this under Ubuntu?

---

### Post by P3t3r on 2012-04-27
uh, anyone?

---

### Post by josephmills on 2012-04-27
Have fun 
[http://www.phoronix-test-suite.com/](http://www.phoronix-test-suite.com/)

---

### Post by P3t3r on 2012-05-03
> **josephmills said:**
> Have fun 
[http://www.phoronix-test-suite.com/](http://www.phoronix-test-suite.com/)

Thanks... but what test should I use for this? I see dozens of tests with label "Graphics" but most tests seem to

1) show purely graphical/speed results, while I want to test correctness/stability (for computing reasons). My eye is not quick enough to notice a failed pixel in a fraction of a second, but computing results on these cards will be disturbed by this. So I would need something that does a bunch of computations and then verifies them to see if the GPU provided the correct results.

2) do not make clear whether they test ALL graphics cards, or just the first one. I need a test that can test all graphics cards (one by one is fine, e.g. first "test -gpu 0", then "test -gpu 1", etc.)

Which test should I be using for this?

(and as a side question: how should I view the test results? It asks me if I want to save, saying no quits the program, saying yes asks more info and then quits the program... how do I get the results of any test?)

---

### Post by P3t3r on 2012-05-06
For later reference: [http://folding.stanford.edu/English/DownloadUtils](http://folding.stanford.edu/English/DownloadUtils)
MemtestCL is a possible test. It's more aimed at memory than at shaders but ok, it'll have to do for now. Apparently one needs windows for a good shader test.

---

