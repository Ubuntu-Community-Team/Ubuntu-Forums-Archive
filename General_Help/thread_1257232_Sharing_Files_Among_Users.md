---
title: "Sharing Files Among Users"
date: 2009-09-03
forum: General Help
---

### Post by techiewannabe on 2009-09-03
I have lots of files, particularly photos, that I would like to share with other users. For example, my wife has her own log-in screen and I would like for her to be able to use our photos (in my files) for her desktop. 

Your help would be appreciated.

Tom

---

### Post by bacardiandwatermelon on 2009-09-03
To keep my filesystem sort of together I created a folder at /home/share to share files between users. You have to make sure the other users can read and write to that directory too. :-)

---

### Post by techiewannabe on 2009-09-03
Thanks for your prompt reply, brandiandwatermelon.

I've created a file entitled, "Share," but I'm not certain how to make it accessible to the other users. I right click the file. I click on 'Permissions.' When I go to 'Group,' or anywhere, in fact, I don't see the names of the other users for whom I want to provide access. 

Ideas?

Thanks.

Tom

---

### Post by bodhi.zazen on 2009-09-03
You have several options. IMO acl (access control lists) are best.

ACL lists (Access Control Lists) ie extended permissions :
    [http://tlug.dnho.net/?q=node/171](http://tlug.dnho.net/?q=node/171)

    [http://ubuntuforums.org/showthread.php?t=145741](http://ubuntuforums.org/showthread.php?t=145741)
   
   The second link is a nice discussion, see pot #9 for ACL.

    GUI tool : eiciel

---

### Post by techiewannabe on 2009-09-03
Thanks, bodhi:
I will give it a try this evening, or tomorrow morning, and let you know how it goes.
I'll have to use the GUI you mentioned. I'm too much of a newbie to use the terminal!
Tom

---

### Post by techiewannabe on 2009-09-03
I tried the GUI but got an error message saying that my system doesn't support that program. (I'm using 9.04.)

Are there any other programs that lend itself to file sharing? Am I to assume that sharing files between Linux users on the same computer is not very common?

Thanks for your help with this.

Tom

:confused:

---

### Post by bodhi.zazen on 2009-09-03
eiciel is in the repositories

[http://ns2.canonical.com/jaunty/eiciel](http://ns2.canonical.com/jaunty/eiciel)

---

### Post by snakepit # on 2009-09-03
> **techiewannabe said:**
> Thanks for your prompt reply, brandiandwatermelon.

I've created a file entitled, "Share," but I'm not certain how to make it accessible to the other users. I right click the file. I click on 'Permissions.' When I go to 'Group,' or anywhere, in fact, I don't see the names of the other users for whom I want to provide access. 

Ideas?

Thanks.

Tom

man chmod

---

### Post by snakepit # on 2009-09-03
> **techiewannabe said:**
>  Am I to assume that sharing files between Linux users on the same computer is not very common? 

Sharing files is a core UN*X philosophy.

# mkdir /home/share
# chmod 777 share

---

### Post by techiewannabe on 2009-09-04
Thanks, bodhi and snakepit for your comments.

Bodhi, I did install Eiciel from the repository. After I installed it and tried to run it, I got the error message. Perhaps I'm doing something wrong within the Eiciel program. (?)

Snakepit: I suspect that you've given me solutions to my problem with your text at the bottom of your notes. Unfortunately, I'm such a newbie (and Linux moron) that I'm not clear on how to take advantage of your advice. I haven't yet worked in the terminal window. (I've had Ubuntu installed for about a month.) Do you know of a simple tutorial that can help a newbie navigate the terminal window?

Thanks.

Tom

---

### Post by bodhi.zazen on 2009-09-04
> **techiewannabe said:**
> Bodhi, I did install Eiciel from the repository. After I installed it and tried to run it, I got the error message. Perhaps I'm doing something wrong within the Eiciel program. (?)

No, but you should probably file a bug report. One question, did you enable acl ? edit /etc/fstab, add "acl" to the options column (4th one) and reboot.

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by techiewannabe on 2009-09-04
Thanks, bodhi.

I'll try it this evening.

Tom

---

