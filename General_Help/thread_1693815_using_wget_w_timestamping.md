---
title: "using wget w/ timestamping"
date: 2011-02-23
forum: General Help
---

### Post by wjcorbin on 2011-02-23
I'm currently using wget to keep a running mirror of another site but I don't have much space locally.  I was wondering if there was a way to turn on -N (timestamping) so that only the "updates" were retrieved (i.e. new/modified files) without hosting a local mirror.

Does -N take a timestamp parameter that will pull any new/modified files after "x"?

It seems like a waste to compare remote file headers against a timestamp without presenting the option of supplying that timestamp.  Supplying a timestamp would allow me to not keep a local mirror and still pull updates that occurred after the desired timestamp.

Any help here would be greatly appreciated.

---

### Post by Habitual on 2011-02-23
Do they have to be "timestamped" to be considered "newer"?

Here's an idea:
Start with a known "good" copy of the target files on the local system.
Hash those files and store the hash values with:
```
md5sum * > md5sum.out
```

Write a shell script that (This is Pseudo-Code)
wget the remote file 
compares it to the md5sum value in md5sum.out
If it's identical, remove it.
else, keep it because it's been changed.

This [-->search<--]("http://www.google.com/custom?num=100&hl=en&newwindow=1&client=google-coop-np&cof=FORID%3A13%3BAH%3Aleft%3BCX%3ASearch%2520Linux%2520Dork%2520Sites%3BL%3Ahttp%3A%2F%2Fwww.google.com%2Fintl%2Fen%2Fimages%2Flogos%2Fcustom_search_logo_sm.gif%3BLH%3A30%3BLP%3A1%3BKMBOC%3A%23336699%3B&adkw=AELymgXJbYVR76SW2w9bRa2Fnh3MxbsVC6XUDif246lkWR0CN1FmUFmZqn2eZD3-sPcFbj0U7sx8UQgVRrkmKIxt2IZzAMHeYkZl2LEHsJRUrR-qupknyaE&boostcse=0&q=md5sum&btnG=Search&cx=017318618393486178147%3Ansves0pzliw") should help.

Sorry if that's generic, but I have to leave something for you to "do". :)

Reference: 
[http://www.go2linux.org/md5sum-how-to-check-file-integrity](http://www.go2linux.org/md5sum-how-to-check-file-integrity)

That should get you started.

Hope that helps.

---

### Post by wjcorbin on 2011-02-24
That might work... thanks for the suggestion.  Hash files would be a lot smaller than the files themselves, and at a bare minimum this may be a workable solution.  

I'm assuming this would envolve the -e command which i've never used, and hopefully that gets executed after each file, and not after the entire recursion... shouldn't take long to test that.

Thanks for the help tho man.  At least its a step in the right direction.  Its more space efficient, but less time efficient (the bitter struggle in this world) since i'm still downloading the entire site plus running hashing/comparison algorithms on each file.  

If anyone knows of a way to specify a datetime to wget where only remote files with lastModified headers newer than the specified time are downloaded, I could be both space and time efficient.

Thanks again.

---

### Post by Habitual on 2011-02-24
Linux is all about options.

The method I proposed saves you from downloading the entire site in favor of 1 file at a time.

Others may have a more elegant solution.

Always glad to be of help, when|where I can.

Good luck.

---

