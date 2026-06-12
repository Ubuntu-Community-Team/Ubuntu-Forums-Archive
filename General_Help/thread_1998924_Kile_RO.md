---
title: "Kile R/O"
date: 2012-06-07
forum: General Help
---

### Post by peterson43 on 2012-06-07
I'm having trouble editing one of my .tex files in Kile. I have the .tex file in a dropbox folder that I share with a collaborator. I have 3 different computers that I myself use (all run Ubuntu). On two of the computers when I open the .tex file in Kile everything works fine. However, with the third computer when I open the .tex file in Kile it seems to be in read only mode and I can't edit it (at the bottom right of the screen it says "R/0").

I can edit other .tex files from Dropbox with Kile on that same computer just fine. Also, I can edit the problem file with other editors (such as Emacs) so it doesn't seem to be a problem with the permissions. 

I did some searching online and I found these two sites that seem to indicate that the problem might be that my collaborator is using some other editor that is encoding the file in some non-utf8 chars. 
[http://forum.kde.org/viewtopic.php?f=20&t=90332]("http://forum.kde.org/viewtopic.php?f=20&t=90332")
[http://sourceforge.net/mailarchive/forum.php?thread_name=4CA37B19.6050805%40gmail.com&forum_name=kile-devel]("http://sourceforge.net/mailarchive/forum.php?thread_name=4CA37B19.6050805%40gmail.com&forum_name=kile-devel")

How do I remove the non-utf8 chars from my file? 
However, both of these references seemed to indicate that removing the non-utf8 chars seemed to fix the problem for them. Also, I don't want to have to remove these characters everytime my collaborator modifies the file. Is there a better fix? Also, Kile running on my other two computers (also running Ubuntu) has no problem with this file. Is there a way to get Kile to simply ignore the issue of non-utf8 chars? 

One thing that I should mention is that the computers that can correctly read the file in Kile are running Ubuntu 11.04 and 11.10, and the one that can't is running Ubuntu 12.04 (they probably have different versions of Kile then too).

---

### Post by peterson43 on 2012-06-07
Update:

I updated one of my computers from 11.04 to 11.10 and then 12.04 and that computer still is able to modify the problem .tex file in Kile. So it doesn't seem to be an issue with running a different version of Ubuntu (or Kile). I suspect I have some strange option turned on in Kile in the computer that is giving me problems.

---

### Post by peterson43 on 2012-06-07
I did notice that after I updated the computer to Ubuntu 12.04 when I opened the file in Kile a message popped up that said there were "too long lines" and that because of that the file was opened in read only mode. However, it doesn't seem to be in read only mode since I can edit and compile the file in Kile just fine.

---

### Post by pistori on 2012-07-01
> **peterson43 said:**
> I did notice that after I updated the computer to Ubuntu 12.04 when I opened the file in Kile a message popped up that said there were "too long lines" and that because of that the file was opened in read only mode. However, it doesn't seem to be in read only mode since I can edit and compile the file in Kile just fine.

I'm facing this (very annoying) problem now just after upgrading to 12.04. In my case, several .tex are now being opened in read-only mode (in kwrite and kile). Kile is giving me the "too long lines" message as well. In my case, I simple can not edit the file anymore.

---

### Post by pistori on 2012-07-01
> **peterson43 said:**
> Update:

I updated one of my computers from 11.04 to 11.10 and then 12.04 and that computer still is able to modify the problem .tex file in Kile. So it doesn't seem to be an issue with running a different version of Ubuntu (or Kile). I suspect I have some strange option turned on in Kile in the computer that is giving me problems.

Everything was working well for me till 11.10 and now I have problems both with kwrite and kile (both are openning my .tex files in read-only mode). And so, I don't thing it is a kile related problem (maybe a kde problem). I will try gedit ...

---

