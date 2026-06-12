---
title: "mogrify -crop creates manure on my hard drive"
date: 2011-04-03
forum: General Help
---

### Post by chrisstankevitz on 2011-04-03
```
$ ls test*
test.png
```

```
mogrify -crop 640x480 test.png
```

```
$ ls test*
test-0.png   test-12.png  test-1.png  test-4.png  test-7.png
test-10.png  test-13.png  test-2.png  test-5.png  test-8.png
test-11.png  test-14.png  test-3.png  test-6.png  test-9.png
```

Expected:
```
$ ls test*
test.png
```

Conclusion: "mogrify -crop" sucks.

Chris

---

### Post by Queue29 on 2011-04-03
I think you have to give it X and Y offsets, otherwise it crops the image into tiles. 

```
mogrify -crop {Width}x{Height}+{X}+{Y} image.png
```

---

