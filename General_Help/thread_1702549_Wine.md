---
title: "Wine"
date: 2011-03-07
forum: General Help
---

### Post by groogrux on 2011-03-07
Hello everyone.  I just installed Ubuntu 10.10 (32 bit) a little less than a week ago (dual-booting with windows 7) and so far everything aside from a little sound issue (resolved) has been great.  Being that I have used Windows for a long time, I have been doing a little research on WINE in order to potentially run iTunes and maybe a game here or there.  I know a lot of people have asked something like this, but how great is my risk for getting a windows virus or malware if all I run through WINE is iTunes or WoW?  Also, is there any risk in getting a virus if I don't ever use WINE with a browser, and only use Chrome or Firefox on Ubuntu to browse the internet?  Sorry to throw out so many questions, but I couldn't find an answer to this anywhere.  Thank you very much!

P.S. Just to clarify, WINE does not run in the background all of the time does it?  Is it just like opening an application?

---

### Post by ubudog on 2011-03-08
The probability of getting a virus is very low.  Wine creates it's own virtual "C:" drive, so yeah, it's pretty hard to get a virus.  If you're super paranoid about that though, you may want to get a virus scanner like ClamAV.

Also, I don't believe I've ever seen Wine running in the background, but I'm not positive about that.

I hope that helps you!  :-)

PS: Welcome to the forums and to the community!

---

### Post by groogrux on 2011-03-08
> **ubudog said:**
> The probability of getting a virus is very low.  Wine creates it's own virtual "C:" drive, so yeah, it's pretty hard to get a virus.  If you're super paranoid about that though, you may want to get a virus scanner like ClamAV.

Also, I don't believe I've ever seen Wine running in the background, but I'm not positive about that.

I hope that helps you!  :-)

PS: Welcome to the forums and to the community!

Awesome. I guess my paranoia just comes from being a Windows user for so long :-P  Thank you for your quick reply!

---

### Post by mastablasta on 2011-03-08
> **groogrux said:**
> Hello everyone. I just installed Ubuntu 10.10 (32 bit) a little less than a week ago (dual-booting with windows 7) and so far everything aside from a little sound issue (resolved) has been great. Being that I have used Windows for a long time, I have been doing a little research on WINE in order to potentially run iTunes and maybe a game here or there. I know a lot of people have asked something like this, but how great is my risk for getting a windows virus or malware if all I run through WINE is iTunes or WoW? Also, is there any risk in getting a virus if I don't ever use WINE with a browser, and only use Chrome or Firefox on Ubuntu to browse the internet? Sorry to throw out so many questions, but I couldn't find an answer to this anywhere. Thank you very much!
 
P.S. Just to clarify, WINE does not run in the background all of the time does it? Is it just like opening an application?
 
 
everything that happens in WINE stays in WINE. :-)
 
so if oyu run a browser through WINE (for example Internet Explorer) and the browser picks up something then you will have the virus in the WINE folder. However it iwll not affect teh system as Linux has ifferent paths, libraries.... basicly everythign different than windows.
 
yah it's just like applicaiton. i am not sure if you ever tried an emulator (virtual box, dos box) - it would be quite similar.

---

### Post by groogrux on 2011-03-08
Perfect.  Thanks for the info everyone.  You've been very helpful.  Just installed WINE, and everything seems to be functioning properly :D

---

### Post by zeezee22 on 2011-03-08
Ubuntu!

To the fellow Ubuntu Gods... Ubuntu!

(yes, I've just finished reading about the Ubuntu name, and I find that I like that much better that a boring old 'hello')

I am installed for about 2 days now and am dedicated to getting off the closed source gear and showing others to do the same.

On the subject of 'Wine'... mine here cracks an absolute monkey whenever I start it up, or at least, think I do.

So I go into c: drive looking at familiar sights and I get excited upon seeing an old friend such a 'notepad', and I click and get (quotes "" added);

"Archive:  /home/zeezee22/.wine/dosdevices/c:/windows/notepad.exe
[/home/zeezee22/.wine/dosdevices/c:/windows/notepad.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /home/zeezee22/.wine/dosdevices/c:/windows/notepad.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /home/zeezee22/.wine/dosdevices/c:/windows/notepad.exe or
          /home/zeezee22/.wine/dosdevices/c:/windows/notepad.exe.zip, and cannot find /home/zeezee22/.wine/dosdevices/c:/windows/notepad.exe.ZIP, period."

and I begin to wonder that perhaps it's not so simple!

Now, in composing ur reply, pls be conscious of the fact that altho I may have once known what to do whilst engaged in computing activity, I currently have NFI, including of that mystery device aka "terminal" - so please (temporarily) think of a 5yr old before you speak - I'll soak up the rest of the forum soon enough.

Thanx in advance,

Zz

---

### Post by zeezee22 on 2011-03-08
Oh! I've worked it out now.

*claps loudly*

I feel so silly. :KS

---

### Post by ubudog on 2011-03-10
> **groogrux said:**
> Awesome. I guess my paranoia just comes from being a Windows user for so long :-P  Thank you for your quick reply!

Lol, it was like that for me when I first switched over.   :p

---

