---
title: "where's the install gone !"
date: 2011-01-26
forum: General Help
---

### Post by chrisbryan on 2011-01-26
Hi All,
I have enjoyed using ubuntu 10.04, it crashed the other day and I did a boot up from a c.d, as I thought it might be able to do a repair, now unbeknownst to me  doing it this way caused me to install a second ubuntu operating system that is now the main system on the computer and windows is the second choice. This in itself doesn't bother me and on finding out that I had 2 ubuntum operating systems on the computer I deleted the one that was in an ordinary folder on the windows programme which is fine but the question is where is the one installed from the cd that I am using now. Help please. Also I know you can print  address labels on office org, but it is a bit hit and miss, is there a programme similar to Avery design available for ubuntu. Any help would be appreciated. Thanks in anticipation  of any help forth coming

---

### Post by oldfred on 2011-01-26
Post this so we can see what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by chrisbryan on 2011-01-26
hi oldfred I don't understand what you are asking me to do, sorry I am not an expert by any lengths of the inmagination

---

### Post by Vaphell on 2011-01-26
go to the linked page and follow the instructions, it's in plain english and rather straightforward
once you do that, paste the result here so someone can look at it and diagnose the problem.

---

### Post by chrisbryan on 2011-01-26
sorry I haven't got a clue what all this is about, everything is working o.k I just wondered where the install was on the hard drive, it has taken me hours to get the printer working, and I can't afford to spend more time trying to figure this out. I do like ubuntu but it is a shame that it is so complicated. So while it is working I will carry on using it and if and when anything goes wrong I will just format the hard dive and wipe it all out and re install Windows XP pro and ubuntu along side like I did originally. No Sweat but its doing my head in I just thought someone who has had more experience would know where on the hard drive this was installed.

---

### Post by Vaphell on 2011-01-26
if you followed the instructions we would get to know what your setup looked like because the procedure was all about generating the report on your configuration. We are not magicians here, we actually need that hard data to give plausible explanations and possible fixes and you provided none.

---

### Post by chrisbryan on 2011-01-27
its o.k Vaphell, no need to get the big stick out it was just  a casual enquiry, I don't expect miracles as I am trying to learn about ubuntu, having loaded the ubuntu os from a folder before I know where that goes to and can find it every time, this is the first time that I have loaded the os from a C.D. The problem with that programme that has been recommended to search the computer to see what is where, is that there is no down loaded ubuntu os folder on the hard drive whatsoever as it was initially saved, scanned for viruses, then burnt to a C.D. and  then I deleted it. I have looked in all the hidden files manually while XP is loaded done a files and folder search in XP but that doesn't cover the hidden files and I have looked in the hard drive contents when ubuntu is loaded and I can't see anything that says wubi, ubuntu, grub, or anyhting that sounds like it's anything to do with ubuntuetc etc. But everything is working fine, but I just like to know where everything is, but if it aint to be I'll put it down to it's just one of those things that will resolve itself in the fullness of time providing we live long enough, and that's the trick LIVING LONG ENOUGH !!!!
All the best Chris
 sudo bash [I HAVEN'T GOT A DOWNLOAD FOLDER !!!]/boot_info_script*.sh  so the response will give no such file or folder

---

### Post by oldfred on 2011-01-27
It downloads to desktop or Downloads on the liveCD. If you turn off the liveCD then it is gone.

Applications, Accessories, Terminal
cd Downloads
sudo bash boot_info_script055.sh

If you hit tab after typing a few characters it will complete line with as many unique characters as it can.

---

### Post by chrisbryan on 2011-01-27
hi oldfred, thanks for your patience and effort to help, I am afraid I don't understand this ubuntu command line and all that jazz if I cut and paste the  sudo bash boot_info_script055.sh into the terminal it just comes as no such file etc . Don't worry like I said in my last post it will all reveal its self in the end and if it doesn't  as Jack Burton said "What The Hell" 
(Big Trouble In Little China)
Regards Chris Bryan

---

