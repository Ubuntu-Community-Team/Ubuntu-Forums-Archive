---
title: "Tar file between Fedora and Windows"
date: 2010-05-08
forum: General Help
---

### Post by billylcm on 2010-05-08
Hi all,

I've also posted it on Fedora forum: [link]("http://forums.fedoraforum.org/showthread.php?t=244891")

The problem I have is I couldn't correctly read a tar file on Windows that was created in Fedora (and Ubuntu 9.10) with some Non-English files. These tar are sure to be extracted correctly on another Fedora (and Ubuntu 9.10) systems however I fail to do so when I tried on some Windows base software such as 7-Zip, GNUWin32 gtar, GNUWin32 libarchive, these software seems can only extract file with ANSCII naming manner.

Here is what I did:

By default, Fedora (and Ubuntu 9.10) system has LANG set to en_US.UTF-8
And here is the files to be tar'ed.
```
-rw-rw-r-- 1 linfmy linfmy 324 2010-05-09 11:37 &#12383;&#12385;&#12354;&#12364;&#12428;&#26085;&#26412; &#20013;&#30033;&#28165;&#27663;&#12434;&#25793;&#31435;.txt
-rw-rw-r-- 1 linfmy linfmy 228 2010-05-09 11:40 &#26222;&#22825;&#38291;&#35347;&#32244;&#12398;&#20840;&#22269;&#20998;&#25955;&#12434;&#26908;&#35342;.txt
```I tar them up with command:
```
$ tar cf output.tar --remove-files *.txt
```A file output.tar was created, and tested with command:
```
$ tar xf output.tar
```No problem so far, all files was correctly extracted. However when I copy these files into a Windows 7 (also Windows XP) and try with software I mentioned above, the file became:
```
09/05/2010  11:40 AM 228 µÖ«Õñ®ÚûôÞ¿ôþÀ&#9508;Òü«Õà¿Õø¢ÕêåµòúÒéÆµñ£Þ¿Ä.txt
09/05/2010  11:37 AM 324 Òü&#402;ÒüíÒüéÒüîÒéîµùÑµ£¼ õ©¡þòæµ©àµ&#9617;ÅÒéÆµôüþ½ï.txt
```Is it a software or OS bug? I've also tried Dar (Disk ARchive), which provides tools both Linux and Windows, but still, the content couldn't be extracted correctly under Windows.

At the moment, the only solution I found is to archive files with genisoimage tool and generate ISO file to be used for both Windows and Fedora (and Ubuntu 9.10) systems...:(

Thanks for all of your helps:)

---

### Post by dcstar on 2010-05-09
> **billylcm said:**
> Hi all,

I've also posted it on Fedora forum: [link]("http://forums.fedoraforum.org/showthread.php?t=244891")
........

Good, leave it there as this is an **Ubuntu** forum specifically for **Ubuntu** users have issues with their **Ubuntu** systems.

---

### Post by billylcm on 2010-05-09
> **dcstar said:**
> Good, leave it there as this is an **Ubuntu** forum specifically for **Ubuntu** users have issues with their **Ubuntu** systems.

Hi,

Thanks(?) for your reply:shock:. The reason I posted it on both forums is because I use both systems (Fedora 12 & Ubuntu 9.10) simultaneously and get the same problem, and was hoping someone could solve the problem and I will share it with others from other forum.
I will edit my post, add 'Ubuntu' key word to get the permission to ask this question here.

---

### Post by billylcm on 2010-05-10
Originally Posted by [**jpollard**]("http://forums.fedoraforum.org/showthread.php?p=1358170#post1358170")
> I think it is a font issue - where ls is identifying a UTF-16 font, and switching.

Windows isn't doing that.

Samba could be identifying it as UTF-16, and sending a font change flag at the
beginning of the file name.

Could be wrong though.Hi,

Thanks for your hints, after a bit of researchs, rather say font issue, it's an encoding issue, due to lack of developes, softwares I used don't handle the name convesion between UTF-16 and UTF-8 properly, where cygwin can do it, it mentions [here]("http://www.cygwin.com/cygwin-ug-net/using-specialnames.html"). Although it cannot display wide char file name in terminal, but is enough for me to use.

---

