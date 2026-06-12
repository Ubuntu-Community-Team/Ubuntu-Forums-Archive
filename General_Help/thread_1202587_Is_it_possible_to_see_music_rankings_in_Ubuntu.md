---
title: "Is it possible to see music rankings in Ubuntu?"
date: 2009-07-02
forum: General Help
---

### Post by paladaxar on 2009-07-02
There are a few good things about Windows (please don't throw bricks at me).  One thing that I really like is that I can rate the mp3's in my music library.  Then, I can go into my music folder and sort "by number of stars".  So my music would be sorted with 5 star songs at the top of the list, then 4 stars etc.

I spent a lot of time rating my songs in windows, but I can't seem to find a way to sort them by ranking in Ubuntu.  Actually, I cant even see the rankings at all.  Does anyone know how to do this?  

I know that I could use Windows Media player through Wine, but that's more like a band-aid than a fix.

Any ideas would be greatly appreciated.

---

### Post by TeoBigusGeekus on 2009-07-02
One word:
Rythmbox!!!!

---

### Post by bobince on 2009-07-02
Note that Windows Media Player ‘ratings’ are not normally stored in the MP3 files or the filesystem itself*. Instead, they are stored in a proprietary-format per-user library file that lives in your ‘Documents and Settings’.

So Ubuntu or a media player other than WMP isn't going to be able to see your ratings. They're not designed to be usable outside of Windows/WMP.

(*: that is, unless you tick the ‘Maintain my star ratings as global ratings in files’ option in WMP. This then *does* write the ratings through to ID3 tags in the file when you make them. I'm not sure what other software recognises these particular tags though.)

---

### Post by paladaxar on 2009-07-02
You said that it stores your preferences in documents and settings, but I have used my external hard drive on other computers and the ratings are still there.  So, I must have the global setting on.

Even so, I guess if it saves the info proprietarily, then there's not much I can do...bummer.  Is there any way to rank songs using a format that will stick with the song across operating systems and media players?

---

