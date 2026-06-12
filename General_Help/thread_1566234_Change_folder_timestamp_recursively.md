---
title: "Change folder timestamp recursively"
date: 2010-09-02
forum: General Help
---

### Post by MonkeyWrench32 on 2010-09-02
I was wondering if anyone knows how to change the timestamps of folders recursively based on the latest timestamp found of the files in that folder.

So for example:

```
jon@UbuntuPanther:/media/media/MP3s/Foo Fighters/(1997-05-20) The Colour and The Shape$ ls -alF
total 55220
drwxr-xr-x  2 jon jon    4096 2010-08-30 12:34 ./
drwxr-xr-x 11 jon jon    4096 2010-08-30 12:34 ../
-rw-r--r--  1 jon jon 1694044 2010-04-18 00:51 Foo Fighters - Doll.mp3
-rw-r--r--  1 jon jon 3151170 2010-04-18 00:51 Foo Fighters - Enough Space.mp3
-rw-r--r--  1 jon jon 5004289 2010-04-18 00:52 Foo Fighters - Everlong.mp3
-rw-r--r--  1 jon jon 5803125 2010-04-18 00:51 Foo Fighters - February Stars.mp3
-rw-r--r--  1 jon jon 4994903 2010-04-18 00:51 Foo Fighters - Hey, Johnny Park!.mp3
-rw-r--r--  1 jon jon 4649556 2010-04-18 00:52 Foo Fighters - Monkey Wrench.mp3
-rw-r--r--  1 jon jon 5216923 2010-04-18 00:51 Foo Fighters - My Hero.mp3
-rw-r--r--  1 jon jon 4294291 2010-04-18 00:52 Foo Fighters - My Poor Brain.mp3
-rw-r--r--  1 jon jon 6778011 2010-04-18 00:52 Foo Fighters - New Way Home.mp3
-rw-r--r--  1 jon jon 2956287 2010-04-18 00:51 Foo Fighters - See You.mp3
-rw-r--r--  1 jon jon 2730072 2010-04-18 00:51 Foo Fighters - Up in Arms.mp3
-rw-r--r--  1 jon jon 6086821 2010-04-18 00:51 Foo Fighters - Walking After You.mp3
-rw-r--r--  1 jon jon 3033660 2010-04-18 00:52 Foo Fighters - Wind Up.mp3
```

The folder "(1997-05-20) The Colour and The Shape" would have its timestamp set to 2010-04-18 00:52.

---

### Post by dcstar on 2010-09-03
> **MonkeyWrench32 said:**
> I was wondering if anyone knows how to change the timestamps of folders recursively based on the latest timestamp found of the files in that folder.

So for example:

```
jon@UbuntuPanther:/media/media/MP3s/Foo Fighters/(1997-05-20) The Colour and The Shape$ ls -alF
total 55220
drwxr-xr-x  2 jon jon    4096 2010-08-30 12:34 ./
drwxr-xr-x 11 jon jon    4096 2010-08-30 12:34 ../
-rw-r--r--  1 jon jon 1694044 2010-04-18 00:51 Foo Fighters - Doll.mp3
-rw-r--r--  1 jon jon 3151170 2010-04-18 00:51 Foo Fighters - Enough Space.mp3
-rw-r--r--  1 jon jon 5004289 2010-04-18 00:52 Foo Fighters - Everlong.mp3
-rw-r--r--  1 jon jon 5803125 2010-04-18 00:51 Foo Fighters - February Stars.mp3
-rw-r--r--  1 jon jon 4994903 2010-04-18 00:51 Foo Fighters - Hey, Johnny Park!.mp3
-rw-r--r--  1 jon jon 4649556 2010-04-18 00:52 Foo Fighters - Monkey Wrench.mp3
-rw-r--r--  1 jon jon 5216923 2010-04-18 00:51 Foo Fighters - My Hero.mp3
-rw-r--r--  1 jon jon 4294291 2010-04-18 00:52 Foo Fighters - My Poor Brain.mp3
-rw-r--r--  1 jon jon 6778011 2010-04-18 00:52 Foo Fighters - New Way Home.mp3
-rw-r--r--  1 jon jon 2956287 2010-04-18 00:51 Foo Fighters - See You.mp3
-rw-r--r--  1 jon jon 2730072 2010-04-18 00:51 Foo Fighters - Up in Arms.mp3
-rw-r--r--  1 jon jon 6086821 2010-04-18 00:51 Foo Fighters - Walking After You.mp3
-rw-r--r--  1 jon jon 3033660 2010-04-18 00:52 Foo Fighters - Wind Up.mp3
```

The folder "(1997-05-20) The Colour and The Shape" would have its timestamp set to 2010-04-18 00:52.

```
man touch
```

---

