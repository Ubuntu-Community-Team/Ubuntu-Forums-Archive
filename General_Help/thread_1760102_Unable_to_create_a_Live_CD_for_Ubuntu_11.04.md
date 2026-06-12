---
title: "Unable to create a Live CD for Ubuntu 11.04"
date: 2011-05-16
forum: General Help
---

### Post by altkon on 2011-05-16
From the following link I have downloaded "Ubuntu 11.04 desktop 
i386" in rar form but when I unrar it I cannot find the ISO file to create a Live CD as the only one that can be burned with Nero is the rar file stated above.
Or else wubi.exe or USB creator .exe.

Please let me know how I can go around this issue.



[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

---

### Post by timothy48342 on 2011-05-16
What do you mean you downloaded it "in rar form?"

Don't open or extract anything, just save it. (the iso)

It is not a .rar. WinRar may have usurped some control that it shouldn't have.

Explain exactly what happens when you click this or that.

Here is a a thead about what might be a similar problem:
[http://ubuntuforums.org/showthread.php?t=1758745](http://ubuntuforums.org/showthread.php?t=1758745)

--t

---

### Post by altkon on 2011-05-16
You are right after step 1 downloaded and saved it on my desktop
but it looks to be a Winrar type file so I thought I should
first extract the ISO image file in order to burn it with Nero6 Burning ROM but I could not find an ISO file amongst extracted
files.
However as explained in the link you refered me to, the saved
file on my desktop, after downloading, is the iso image file and
Nero6 recognizes it as such for burning only it warns me of some error in the files length to be corrected or ignored.
Since you recommend it I will ignore it and go ahaead with burning process and will let you know if succesfully accomplished.:confused: 
Thanks.
AA

---

### Post by altkon on 2011-05-16
You are right after step 1 downloaded and saved it on my desktop
but it looks to be a Winrar type file so I thought I should
first extract the ISO image file in order to burn it with Nero6 Burning ROM but I could not find an ISO file amongst extracted
files.
However as explained in the link you refered me to, the saved
file on my desktop, after downloading, is the iso image file and
Nero6 recognizes it as such for burning only it warns me of some error in the files length to be corrected or ignored.
Since you recommend it I will ignore it and go ahaead with burning process and will let you know if succesfully accomplished.:confused: 
Thanks.
AA

---

### Post by pricetech on 2011-05-16
You should probably check the downloaded file against the checksum available from the Ubuntu site.

Also, use the slowest speed offered by your burner software and use the test disk option once you boot, before installing.

Have fun.

---

### Post by mikewhatever on 2011-05-16
Here is a very similar thread with the OP thinking the downloaded file to be a ZIP archive.
[http://ubuntuforums.org/showthread.php?t=1758745](http://ubuntuforums.org/showthread.php?t=1758745)

---

### Post by altkon on 2011-05-16
I have downloaded it twice in order to cross check the size and I found out that the packed size of the one is 638 MB and of the other 698 MB so I am going to choose the bigger one.
But I dont know how to use the test disk option before installing
it.??
Can you guide me please??:cool:

---

### Post by altkon on 2011-05-16
Sorry I forgot to mention that the bigger size image Iso file is
called Kubuntu iso Ubuntu.

---

### Post by timothy48342 on 2011-05-16
> **altkon said:**
> Sorry I forgot to mention that the bigger size image Iso file is
called Kubuntu iso Ubuntu.

Are you sure you downloaded each from the same link?
If you download it twice in the same way it they should be identicle.
Don't just pick the larger one hoping you have a greater than 50% chance  of it being a good file. You want 100%. A damaged file, burnt, then  used is asking for mysteriuos hard to figure out errors later.

Check the checksum like someone above said. And make sure your downloaded the exact file you want. (desired version, etc)

--timothy48342

---

### Post by altkon on 2011-05-17
You are right I have downloaded each file from different links
as shown below.
The 638 MB SIZE is from [www.ubuntu.com](www.ubuntu.com) whereas the 698 MB SIZE
from [www.kubuntu.org](www.kubuntu.org).
I decided to opt burning the one downloaded from [www.ubuntu.com](www.ubuntu.com) site which is the latest version which I want,and because of desktop environment and program differences.
The size of Kbuntu is somewhat bigger by 60MB.
I am going to check the checksum using the winmd5sum program.
Please correct me if I am wrong.
Tks.

[http://www.kubuntu.org/getkubuntu/download](http://www.kubuntu.org/getkubuntu/download)
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

---

### Post by altkon on 2011-05-17
I have installed winmd5sum and when I checked it
shows that chechsums are different..so I guess my file is
corrupted and I should try downloading it again from
[www.ubuntu.com](www.ubuntu.com) or another site if you can suggest me one.

---

### Post by timothy48342 on 2011-05-17
I would think you want to download from ubuntu.com if possible. I'm not too sure about other sources. The BitTorrent links are listed here --> [http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download)
But in my oppinion that is a last resort. (not to hate on BitTorrent. I love bitTorrent.)

If it is just a corrupted download, try it agian. Move the corrupted file (or file suspected of corruption) to another folder and re-download it fresh.

I am a beginner, too and this is educational for me, so I am glad you posted. I've heard people mention hash checking and didn't know what in the world they were talking about... Did a search, found the hases at ([https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)), found the instructions ([https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM))  ...Now I know.

I have just downloaded winMd5Sum and I'm going to check the same file that you are getting. 

You are getting: ubuntu-11.04-desktop-i386.iso
And the hash should be: 8b1085bed498b82ef1485ef19074c281

Is that correct?
I'm at 89% downloaded, on that file, so I'll let you know my results in a bit.
--tim

---

### Post by altkon on 2011-05-17
Yes I am getting 
ubuntu-11.04-desktop-i386.iso
My hash file is
cf7636a571a8a0d58ff753f9c27f1042
Thanks for your support, please keep me posted 
and let me know your results.

---

### Post by timothy48342 on 2011-05-17
ok... I just downloaded it and the hash mached. (Sorry your having trouble.)

I was just thinking...
Truncated downloads are far more common... (since things get  disconnected or canceled) ...compared to actual corruption of the data.  (due to all the automated error checking that takes place)

So, you might check the SIZE of the iso as well. If the size is smaller  than expected, then definately just re-try the download the normal way.
If you are downloading ubuntu-11.04-desktop-i386.iso ,
the size will be 701,724 KB (as displayed by WinXp explorer)
WinXP command prompt (dir) shows it as  718,583,808 bytes.

Is that what you get for the file that you think waas corrupted? (If you didn't already delete it.)

--timothy48342

---

### Post by timothy48342 on 2011-05-17
ok. defiinately retry the download. If you know that you frequently have problems downloading due to a problem with your ... software, hardware, connection, bad weather, ISP, bad luck, etc, etc.... Then just try it a few times.

If you never ever have downloading problems... well... I don't know. This is a stumper.

There is always the "free" CD they can send you for a nominal cost. I remember seeing a link to it and saw a conversation that the cost is just shipping and maybe the cost of the media itself. very cheap.

The only thing is that you have to WAIT for it. Not sure if there are options for expedited shipping, like next-day fexEd or something. That'd be nice at least.

Keep us posted. Maybe someone will pop in with other suggestiong.
-tim

---

### Post by altkon on 2011-05-17
> **timothy48342 said:**
> ok... I just downloaded it and the hash mached. (Sorry your having trouble.)

I was just thinking...
Truncated downloads are far more common... (since things get  disconnected or canceled) ...compared to actual corruption of the data.  (due to all the automated error checking that takes place)

So, you might check the SIZE of the iso as well. If the size is smaller  than expected, then definately just re-try the download the normal way.
If you are downloading ubuntu-11.04-desktop-i386.iso ,
the size will be 701,724 KB (as displayed by WinXp explorer)
WinXP command prompt (dir) shows it as  718,583,808 bytes.

Is that what you get for the file that you think waas corrupted? (If you didn't already delete it.)

--timothy48342
At second trial I have decided to download it from Alternative downloads of Ubuntu.com as mtorent Size 685 MB but when downloaded and run file size shows as 701.742 WINRAR Type.ubuntu-11.04-desktop-i386.iso - ISO9660 archive, unpacked size 717,813,717 bytes
Unfortunately when winmd5sum checked does not match although
hash file 8b1085bed498b82ef1485ef19074c281 identical to yours.
Took the chances and burned it into a CD and when I run it opened 
the usual "Ubuntu Menu" with options for a Demo or Full installation or Install it inside Windows.
Thanks a lot.
AA

---

### Post by timothy48342 on 2011-05-17
It worked?? Yea!!

I hate that there or so many differnt "file sizes" for the same file depending how you check it. However if I right-click properties, then the archive tab, it says 717,813,717 for "total length" and the same for "Packed length" and that's an exact match to your "Unpacked length", so I think your file is NOT truncated. 

One thing... You said winMd5Sum says that the hash does NOT?? match, but that your hash MATCHES mine? I noticed that winMd5Sum does give any feedback if you accidently enter illeagle chacters, like "l", "o", or a space, or if the hash is too short, so you still have to carful with your cut-n-paste.

Oh, well, as long as it was "8b1085bed498b82ef1485ef19074c281" then your all good.

--tim

---

### Post by altkon on 2011-05-18
I think that I am all good too.
What I want to do now is to use the test disk option once I boot, before installing.
But I dont know how to do it??
Please let me know if you can.
Thanks.

---

### Post by timothy48342 on 2011-05-18
Put in the live cd, boot comp.
(If your bois is not set up to boot from cd, then you'll have to mess aound with that.)
As soon as the CD starts to boot, the Ubuntu flash screen comes up. Press and hold shift. And then a "different" screeen come up.
I did it once pressing shift as soon I possibly could and again where I waited a bit and it worked both times, so it should be easy to do. (Unlike trying to get into safe mode on Windows where it's like an arcade game to press the right key at the right time.)

Once the "different" screen come up, there will be text at the bottom describing the function of 6 different F-keys. "F1 Help ... F2 Language ..." etc.
I don't know if this is called "the grub menu" or not, but maybe. LOL

The menu itself was covered up by the language selectin menu when I did it, but just press esc once to make that go away and your see about 5 or 6 choices including, a way to test the disk, test memory, boot Ubuntu, boot the hard drive. Something like that...

So test the disk. I did mine a few times and it said "errors in 1 file" every time, but it doesn't say which file. My CD appears to work fine. I suppose I need to re-burn it before doing a full install.

I just remembered that all this applies to the previos version, (10.?? and you have 11.??) so it might be slighly different. I suppose, since I have 11 downloaded now I may as well burn that one too and see what has changed.

Hope all goes well. I'm off here for the rest of the day. It's been nice comparing notes with ya, altkon. Would do it agian any time.

--timothy48342

---

### Post by altkon on 2011-05-18
Enjoyed our fruitfull coop and look forward to repeat it again.
Will let you know results of my testing whenever I manage to do so.

Presently on my laptop I have a dual boot W7 with Ubuntu 11.04 and I needed this LIVE CD for repair purposes just in case.

Recently I had my Evolution e-mail application corrupted when I tried to import my Address Book contacts. 
So now it refuses to start up and needs reconfiguring in order to work again.

Will keep in touch..

Regards.
AA

---

