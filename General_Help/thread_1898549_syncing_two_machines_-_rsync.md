---
title: "syncing two machines - rsync"
date: 2011-12-21
forum: General Help
---

### Post by Ceiber Boy on 2011-12-21
I have two computers (one Ubuntu and one Mac) that I work on, the Mac is a laptop and Ubuntu is a desktop. I work on either machine according to the circumstance.

I wish to use rsync to synchronise files between the two machines. I'm able without issue to achieve an SSH connection between the two machines. But the issue I am facing is that I don't know which machine has the most updated files on it. Using rsync I've used a different line of code for each file in the home directory (e.g. documents, music etc..). using a script on the desktop I.

1st, rsync all the files from the laptop over to the desktop, example code:

rsync -ur mac@192.168.x.x:/Users/User/Documents/ /home/ubuntu/Documents/

so it copy's all the files from the mac Documents directory to the Ubuntu Documents directory.

2nd, rsync -ur --delete /home/ubuntu/Documents/ mac@192.168.x.x:/Users/mac/Documents/

so it copy's all the files from the Ubuntu desktop to the Mac Documents directory.

now this worked fine until (for example) I have a Document 'test' im working on saved on the desktop, when I move 'test' into the Documents Directory and then run the script to sync the machines 'test' gets recopied from the mac desktop to the Ubuntu desktop and the 'test in Ubuntu's Documents Directory gets copied to Documents directory on the Mac so I end up with four copy's of 'test'.

I hope what im trying to achieve is clear form the explanation so..

is their a way to make these machines sync without having to manually deleting the previously synced file on the other machine? or is their a better way of doing this?

please ask any questions, and or offer any help, I would appreciate it.

---

### Post by JCM_Pico on 2011-12-21
Well I'm assuming that you usually work at home in your Ubuntu desktop and a few times when you need to leave your place you work in the Mac.... If this is the case you should consider :

```
rsync -ur --delete mac@192.168.x.x:/Users/User/Documents/ /home/ubuntu/Documents/
```

In this way your Ubuntu will fetch all the new files in Mac and delete the non existent ones...

But if it isn't the case.... well then I need to think a little more :)

---

### Post by Ceiber Boy on 2011-12-21
> **JCM_Pico said:**
> Well I'm assuming that you usually work at home in your Ubuntu desktop and a few times when you need to leave your place you work in the Mac.... If this is the case you should consider :

```
rsync -ur --delete mac@192.168.x.x:/Users/User/Documents/ /home/ubuntu/Documents/
```In this way your Ubuntu will fetch all the new files in Mac and delete the non existent ones...

But if it isn't the case.... well then I need to think a little more :)

Yes, that's right, i do take the Mac laptop out, however when I do so I also requre all the files on my Mac laptop that i keep on my Ubuntu desktop, and if i use the '--delete' option then i will have to copy from scratch all those files back over to the Mac!

---

### Post by JCM_Pico on 2011-12-21
I'm willing to keep this simple...... So I'm not going to suggest any far fetch script....
Have you ever consider Ubuntu one, dropbox and/or sugarsynk?


But if you want other way I can help you :D

---

### Post by Ceiber Boy on 2011-12-21
> **JCM_Pico said:**
> I'm willing to keep this simple...... So I'm not going to suggest any far fetch script....
Have you ever consider Ubuntu one, dropbox and/or sugarsynk?


But if you want other way I can help you :D
I appreciate the suggestion, but as both machines are on a LAN (and i not allowed to put the files in the public domain!), any further help would be appreciated.

Many Thanks

---

### Post by JCM_Pico on 2011-12-21
It will not work the post that I made... sorry

---

### Post by Ceiber Boy on 2011-12-21
> **JCM_Pico said:**
> It will not work the post that I made... sorry
I'll give this a try tomorrow, and post the result.

Many Thanks

---

### Post by Ceiber Boy on 2011-12-21
> **JCM_Pico said:**
> It will not work the post that I made... sorry
oh..ok..thanks for trying.

---

### Post by JCM_Pico on 2011-12-21
I read with a little more attention the first post..... And I would like to ask you if you tested your method or just mentally did the steps....
> **Ceiber Boy said:**
> ... I have a Document 'test' im working on saved on the desktop, when I  move 'test' into the Documents Directory and then run the script to sync  the machines 'test' gets recopied from the mac desktop to the Ubuntu  desktop and the 'test in Ubuntu's Documents Directory gets copied to  Documents directory on the Mac so I end up with four copy's of 'test'.

I'm asking this because when you run the first rsync the file test wont be replaced in your desktop, since you are using the -u option the newer files in the receiver will be skipped... Then when you run the 2nd rsync the current copy  of test will be updated to the Mac.....

Is this true or I'm not thinking right???

---

### Post by pingvin on 2011-12-21
If you haven't already, have a look at unison. Awesome command-line app - works seamlessly over SSH.

Mike

---

### Post by Ceiber Boy on 2011-12-22
> **JCM_Pico said:**
> I read with a little more attention the first post..... And I would like to ask you if you tested your method or just mentally did the steps....


I'm asking this because when you run the first rsync the file test wont be replaced in your desktop, since you are using the -u option the newer files in the receiver will be skipped... Then when you run the 2nd rsync the current copy  of test will be updated to the Mac.....

Is this true or I'm not thinking right???
it is implemented, and yes your right this dose happern.

---

### Post by JCM_Pico on 2011-12-22
So... it's solved ?

---

