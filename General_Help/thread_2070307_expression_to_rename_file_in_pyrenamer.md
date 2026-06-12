---
title: "expression to rename file in pyrenamer?"
date: 2012-10-12
forum: General Help
---

### Post by qwertyjjj on 2012-10-12
I have about 100 files in the format
24 - 102__1.AM.to.2.AM--
24 - 410__1.AM.to.2.AM--

I can#t figure out the expression in pyrenamer to batch rename them to:
24 - 1x01.avi
24 - 4x10.avi

Any help?

---

### Post by cjhabs on 2012-10-12
What is the "rule" for renaming - it is not obvious to me from your examples

---

### Post by Vaphell on 2012-10-12
classic example of gui programs being convenient until they are not :)

pyrenamer doesn't appear to allow patterns for exact number of characters, only block of numbers/characters/junk. That means that it can't really be done in 1 go. You'd have to
- insert x at 7 in Insert/Delete
- change **{X}_{@}** to **{1}.avi** in Patterns

in terminal using *rename* it would be like this:
```
$ ls -1
24 - 102__1.AM.to.2.AM--
24 - 410__1.AM.to.2.AM--
$ **rename -n 's/(24 - )([0-9])([0-9]{2}).*/$1$2x$3.avi/' *--**
24 - 102__1.AM.to.2.AM-- renamed as 24 - 1x02.avi
24 - 410__1.AM.to.2.AM-- renamed as 24 - 4x10.avi
```
-n means dry run, remove it to perform the operation.

---

### Post by qwertyjjj on 2012-10-13
> **Vaphell said:**
> classic example of gui programs being convenient until they are not :)

pyrenamer doesn't appear to allow patterns for exact number of characters, only block of numbers/characters/junk. That means that it can't really be done in 1 go. You'd have to
- insert x at 7 in Insert/Delete
- change **{X}_{@}** to **{1}.avi** in Patterns

in terminal using *rename* it would be like this:
```
$ ls -1
24 - 102__1.AM.to.2.AM--
24 - 410__1.AM.to.2.AM--
$ **rename -n 's/(24 - )([0-9])([0-9]{2}).*/$1$2x$3.avi/' *--**
24 - 102__1.AM.to.2.AM-- renamed as 24 - 1x02.avi
24 - 410__1.AM.to.2.AM-- renamed as 24 - 4x10.avi
```
-n means dry run, remove it to perform the operation.

I removed -n but it didn#t do anything to the files at all.
No errors either.

```

$ rename 's/(24 - )([0-9])([0-9]{2}).*/$1$2x$3.avi/' *--
j-media-centre@jmediacentre-A880G:/Media/TV Shows/24--$ ls -l
total 60966544
-rw-r--r-- 1 j-media-centre j-media-centre 367095808 Oct  9 03:28 24 - 101_aaa.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367085568 Oct  9 05:50 24 - 102__1.AM.to.2.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367091712 Oct  8 22:10 24 - 103__2.AM.to.3.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367093760 Oct  8 22:04 24 - 104__3.AM.to.4.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367104000 Oct  9 02:39 24 - 105__4.AM.to.5.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367106048 Oct  8 22:36 24 - 106__5.AM.to.6.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367095808 Oct  8 17:45 24 - 107__6.AM.to.7.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367106048 Oct  8 18:23 24 - 108__7.AM.to.8.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 366923776 Oct  8 21:02 24 - 109__8.AM.to.9.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367097856 Oct  8 23:56 24 - 110__9.AM.to.10.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367112192 Oct  8 21:33 24 - 111__10.AM.to.11.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367108096 Oct  9 03:35 24 - 112__11.AM.to.12.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367108096 Oct  9 03:54 24 - 113__12.AM.to.1.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367097856 Oct  9 01:11 24 - 114__1.PM.to.2.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367106048 Oct  9 03:15 24 - 115__2.PM.to.3.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367083520 Oct  8 19:34 24 - 116__3.PM.to.4.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367069184 Oct  9 01:50 24 - 117__4.PM.to.5.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367110144 Oct  9 00:32 24 - 118__5.PM.to.6.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367085568 Oct  9 00:44 24 - 119__6.PM.to.7.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367065088 Oct  9 04:14 24 - 120__7.PM.to.8.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367073280 Oct  8 22:13 24 - 121__8.PM.to.9.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367054848 Oct  9 00:36 24 - 122__9.PM.to.10.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367069184 Oct  9 00:49 24 - 123__10.PM.to.11.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367112192 Oct  9 03:33 24 - 124 - _11.PM.to.12.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 366948352 Oct  8 19:09 24 - 201__8.AM.to.9.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 366850048 Oct  8 19:19 24 - 202__9.AM.to.10.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 366905344 Oct  8 20:54 24 - 203__10.AM.to.11.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367077376 Oct  4 14:29 24 - 204__11.AM.to.12.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367069184 Oct  4 14:29 24 - 205__12.PM.to.1.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367075328 Oct  4 14:29 24 - 206__1.PM.to.2.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367071232 Oct  4 14:29 24 - 207__2.PM.to.3.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367071232 Oct  4 14:29 24 - 208__3.PM.to.4.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367075328 Oct  8 20:51 24 - 209__4.PM.to.5.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 365090816 Oct  8 21:05 24 - 210__5.PM.to.6.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367110144 Oct  8 20:32 24 - 211__6.PM.to.7.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367085568 Oct  8 19:19 24 - 212__7.PM.to.8.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367065088 Oct  8 19:11 24 - 213__8.PM.to.9.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367091712 Oct  9 00:32 24 - 214__9.PM.to.10.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367079424 Oct  9 01:48 24 - 215__10.PM.to.11.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367071232 Oct  8 20:28 24 - 216__11.PM.to.12.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367104000 Oct  8 19:11 24 - 217__12.AM.to.1.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367093760 Oct  9 03:48 24 - 218__1.AM.to.2.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367101952 Oct  8 18:58 24 - 219__2.AM.to.3.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367110144 Oct  9 01:17 24 - 220__3.AM.to.4.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367038464 Oct  8 19:03 24 - 221__4.AM.to.5.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367118336 Oct  8 19:19 24 - 222__5.AM.to.6.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367120384 Oct  9 00:55 24 - 223__6.AM.to.7.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367118336 Oct  8 19:10 24 - 224 - _7.AM.to.8.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 366909440 Oct  9 06:46 24 - 301__1PM.to.2.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367108096 Oct  9 06:48 24 - 302__2PM.to.3.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367071232 Oct  9 06:42 24 - 303__3PM.to.4.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367069184 Oct  9 06:56 24 - 304__4PM.to.5.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367081472 Oct  9 06:47 24 - 305__5PM.to.6.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367112192 Oct  9 06:07 24 - 306__6PM.to.7.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367083520 Oct  9 06:48 24 - 307__7PM.to.8.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367058944 Oct  9 06:00 24 - 308__8PM.to.9.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367056896 Oct  9 06:50 24 - 309__9PM.to.10.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367069184 Oct  9 06:45 24 - 310__10PM.to.11.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367083520 Oct  9 06:47 24 - 311__11PM.to.12.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367112192 Oct  9 06:43 24 - 312__12AM.to.1.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367065088 Oct  9 06:45 24 - 313__1.AM.to.2.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367097856 Oct  9 06:39 24 - 314__2.AM.to.3.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367011840 Oct  9 06:44 24 - 315__3.AM.to.4.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367079424 Oct  9 06:47 24 - 316__4.AM.to.5.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367077376 Oct  9 04:21 24 - 317__5.AM.to.6.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367106048 Oct  9 06:32 24 - 318__6.AM.to.7.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367112192 Oct  9 06:47 24 - 319__7.AM.to.8.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367110144 Oct  9 06:47 24 - 320__8.AM.to.9.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367077376 Oct  9 06:43 24 - 321__9.AM.to.10.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367114240 Oct  9 04:07 24 - 322__10.AM.to.11.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367087616 Oct  9 06:27 24 - 323__11.AM.to.12.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367085568 Oct  9 06:42 24 - 324 - _12.PM.to.1.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 399514758 Oct  5 08:29 24 - 401__7.AM.to.8.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 405997954 Oct  5 08:29 24 - 402__8.AM.to.9.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 407975052 Oct  5 08:28 24 - 403__9.AM.to.10.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 409942098 Oct  5 08:28 24 - 404__10.AM.to.11.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 409000682 Oct  5 08:29 24 - 405__11.AM.to.12.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 408783214 Oct  5 08:29 24 - 406__12.PM.to.1.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 409283610 Oct  5 08:29 24 - 407__1.PM.to.2.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 409199622 Oct  5 08:29 24 - 408__2.PM.to.3.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 402156056 Oct  4 22:00 24 - 409__3.PM.to.4.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 408182082 Oct  4 21:59 24 - 410__4.PM.to.5.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 405860930 Oct  4 21:58 24 - 411__5.PM.to.6.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 409135758 Oct  4 22:00 24 - 412__6.PM.to.7.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 409039292 Oct  4 21:53 24 - 413__7.PM.to.8.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 404638764 Oct  5 08:29 24 - 414__8.PM.to.9.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 401153622 Oct  5 08:29 24 - 415__9.PM.to.10.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 408300480 Oct  5 08:29 24 - 416__10.PM.to.11.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 408904234 Oct  5 08:27 24 - 417__11.PM.to.12.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 401737204 Oct  5 08:29 24 - 418__12.AM.to.1.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 409309730 Oct  5 08:25 24 - 419__1.AM.to.2.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 409093516 Oct  5 08:22 24 - 420__2.AM.to.3.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 409382462 Oct  5 08:29 24 - 421__3.AM.to.4.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 403565918 Oct  5 08:27 24 - 422__4.AM.to.5.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 407657964 Oct  5 08:27 24 - 423__5.AM.to.6.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 407071180 Oct  5 08:26 24 - 424 - _6.AM.to.7.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 724389888 Oct  8 06:07 24 - 501__7.AM.to.8.AM--[HD].avi
-rw-r--r-- 1 j-media-centre j-media-centre 734453234 Oct  8 06:05 24 - 502__8.AM.to.9.AM--[HD].avi
-rw-r--r-- 1 j-media-centre j-media-centre 723390464 Oct  8 06:02 24 - 503__9.AM.to.10.AM--[HD].avi
-rw-r--r-- 1 j-media-centre j-media-centre 722366464 Oct  8 06:00 24 - 504__10.AM.to.11.AM--[HD].avi
-rw-r--r-- 1 j-media-centre j-media-centre 724643840 Oct  8 06:05 24 - 505__11.AM.to.12.PM--[HD].avi
-rw-r--r-- 1 j-media-centre j-media-centre 730646528 Oct  8 06:07 24 - 506__12.PM.to.1.PM--[HD].avi
-rw-r--r-- 1 j-media-centre j-media-centre 733927426 Oct  8 06:06 24 - 507__1.PM.to.2.PM--[HD].avi
-rw-r--r-- 1 j-media-centre j-media-centre 733259776 Oct  8 06:06 24 - 508__2.PM.to.3.PM--[HD].avi
-rw-r--r-- 1 j-media-centre j-media-centre 720953344 Oct  8 06:06 24 - 509__3.PM.to.4.PM--[HD].avi
-rw-r--r-- 1 j-media-centre j-media-centre 717754368 Oct  8 06:07 24 - 510__4.PM.to.5.PM--[HD].avi
-rw-r--r-- 1 j-media-centre j-media-centre 723832832 Oct  8 06:05 24 - 511__5.PM.to.6.PM--[HD].avi
-rw-r--r-- 1 j-media-centre j-media-centre 722819072 Oct  8 06:06 24 - 512__8.PM.to.7.PM--[HD].avi
-rw-r--r-- 1 j-media-centre j-media-centre 733052928 Oct  8 06:07 24 - 513__7.PM.to.8.PM--[HD].avi
-rw-r--r-- 1 j-media-centre j-media-centre 731770880 Oct  8 06:05 24 - 514__8.PM.to.9.PM--[HD].avi
-rw-r--r-- 1 j-media-centre j-media-centre 732774400 Oct  8 06:04 24 - 515__9.PM.to.10.PM--[HD].avi
-rw-r--r-- 1 j-media-centre j-media-centre 725716992 Oct  8 06:05 24 - 516__10.PM.to.11.PM--[HD].avi
-rw-r--r-- 1 j-media-centre j-media-centre 730638336 Oct  8 06:07 24 - 517__11.PM.to.12.AM--[HD].avi
-rw-r--r-- 1 j-media-centre j-media-centre 726331392 Oct  8 06:06 24 - 518__12.AM.to.1.AM--[HD].avi
-rw-r--r-- 1 j-media-centre j-media-centre 729389056 Oct  8 06:06 24 - 519__1.AM.to.2.AM--[HD].avi
-rw-r--r-- 1 j-media-centre j-media-centre 715749376 Oct  8 06:07 24 - 520__2.AM.to.3.AM--[HD].avi
-rw-r--r-- 1 j-media-centre j-media-centre 720351232 Oct  8 06:03 24 - 521__3.AM.to.4.AM--[HD].avi
-rw-r--r-- 1 j-media-centre j-media-centre 728842240 Oct  8 06:03 24 - 522__4.AM.to.5.AM--[HD].avi
-rw-r--r-- 1 j-media-centre j-media-centre 730155008 Oct  8 06:04 24 - 523__5.AM.to.6.AM--[HD].avi
-rw-r--r-- 1 j-media-centre j-media-centre 709961728 Oct  8 06:04 24 - 524 - _6.AM.to.7.AM--[HD].avi
-rw-r--r-- 1 j-media-centre j-media-centre 366989716 Oct  8 19:31 24 - 601__6.AM.to.7.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 369627136 Oct  8 21:15 24 - 602__7.AM.to.8.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 369631232 Oct  8 20:53 24 - 603__8.AM.to.9.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 363048960 Oct  8 18:41 24 - 604__9.AM.to.10.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 366940160 Oct  8 21:08 24 - 605__10.AM.to.11.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367756078 Oct  8 17:45 24 - 606__11.AM.to.12.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367065088 Oct  8 19:25 24 - 607__12.PM.to.1.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 366986940 Oct  8 19:24 24 - 608__1.PM.to.2.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 366986554 Oct  8 20:55 24 - 609__2.PM.to.3.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 366855562 Oct  8 19:06 24 - 610__3.PM.to.4.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 366989930 Oct  8 21:14 24 - 611__4.PM.to.5.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 366984504 Oct  8 21:29 24 - 612__5.PM.to.6.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 366990004 Oct  8 20:49 24 - 613__6.PM.to.7.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 366602240 Oct  8 19:07 24 - 614__7.PM.to.8.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367745024 Oct  8 16:43 24 - 615__8.PM.to.9.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 366989156 Oct  8 19:22 24 - 616__9.PM.to.10.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 368084992 Oct  8 19:12 24 - 617__10.PM.to.11.PM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 366979138 Oct  8 19:22 24 - 618__11.PM.to.12.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367151104 Oct  8 19:08 24 - 619__12.AM.to.1.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 366753792 Oct  8 19:22 24 - 620__1.AM.to.2.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367093760 Oct  8 18:55 24 - 621__2.AM.to.3.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 367831916 Oct  8 19:05 24 - 622__3.AM.to.4.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 365364756 Oct  8 19:39 24 - 623__4.AM.to.5.AM--.avi
-rw-r--r-- 1 j-media-centre j-media-centre 366403584 Oct  8 19:06 24 - 624 - _5.AM.to.6.AM--.avi
j-media-centre@jmediacentre-A880G:/Media/TV Shows/24--$

```

---

### Post by Vaphell on 2012-10-13
the pattern selecting files is wrong.
i took your words literally ("I have about 100 files in the format 24 - 102__1.AM.to.2.AM-- ...") and used ***--**, while it should be ***--.avi** or something like that, even ***** alone should do, seeing all files follow the format.

```
rename 's/(24 - )([0-9])([0-9]{2}).*/$1$2x$3.avi/' *****
```

```
ls -1
24 - 102__1.AM.to.2.AM--.avi
24 - 410__1.AM.to.2.AM--.avi
$ rename 's/(24 - )([0-9])([0-9]{2}).*/$1$2x$3.avi/' *
$ ls -1
24 - 1x02.avi
24 - 4x10.avi
```

---

