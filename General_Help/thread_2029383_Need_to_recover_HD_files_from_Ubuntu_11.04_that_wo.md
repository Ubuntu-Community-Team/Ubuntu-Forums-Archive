---
title: "Need to recover HD files from Ubuntu 11.04 that wont boot"
date: 2012-07-19
forum: General Help
---

### Post by ilivetowin on 2012-07-19
Awhile back my Ubuntu stopped booting and gave me the error message: 

"run-int: /sbin/init: I/O error"

I have not attempted to fix it for awhile and all a sudden today it now reads: 

"BusyBox v1.17.1 (Ubuntu 1:1.17.1-10ubntu1) built in shell (ash) enter help for a list of built in commands" 

I  dont care about getting this thing to boot again, I just need to get  all my files(Docs, Pictures, Videos etc...) off and onto an external. 

When  I load a liveCD, I can see all the files on the drive, but when I tried  to copy my entire home directory over to the external, only about 18gbs  of 200gbs copied. The rest said I didnt have permission. Seemed random  as to which files allowed me permission and which didnt. 

Anyways,  if anyone can help me, it would be greatly appreciated. Again, I just  want to be able to get these files onto an external so I dont lose them.  Keep in mind I am a linux newbie, so I am not too strong with the  command line or advanced stuff, but I am willing to try! 

Thanks. 

Sean

---

### Post by rukiaEnix on 2012-07-19
Just boot with a live CD and get your files out.

---

### Post by rukiaEnix on 2012-07-19
What is the command you are using to copy your files?

---

### Post by ilivetowin on 2012-07-19
Didnt use a command, I just opened up folder, went to the 1TB HD where my files are, clicked the home folder and attempted to drag the home folder into the external hard drive. Problem was, many of the files come up saying I do not have proper permission for these files.

---

### Post by rukiaEnix on 2012-07-19
That is not the right way...

Do it like this:

```

sudo cp -R /home/user /media/external

```Where /home/user is your folder you want to copy, and /media/external your external drive.

---

### Post by ilivetowin on 2012-07-19
I may have screwed something up trying to fix this all day. I should have just posted on here first...

So the folder I want to copy is named "SeanP" I click on folder, went to the home folder, and right clicked on the folder "SeanP" to find its location. Heres what I see:

Name: SeanP
Type: folder(inode/directory)
Contents: 13,162 items, totaling 106.6GB
(some contents unreadable)

Location: /media/314f6070-0529-4b59-8921_____(a bunch more numbers)/home

Is that whole thing starting with /media/314.... what I put in for home? 

The external is listed as: 
Name: SeanP External 
Type: folder(inode/directory)
Location: /media
Volume: SeanP External

so the location there would be /media/SeanP External?

---

### Post by rukiaEnix on 2012-07-19
> 
Is that whole thing starting with /media/314.... what I put in for home? 


Yes

And for external please post the result of this:

```

ls /media

```

---

### Post by ilivetowin on 2012-07-19
Result of ls /media

314f6070-0529-4b59-8921-d9589883438  cdrom  SEANP EXTERNAL

---

### Post by rukiaEnix on 2012-07-19
Then yes, it is SEANP EXTERNAL.

Then the command will be like this:

```

sudo cp -R /media/314f6070-0529-4b59-8921-d9589883438 /media/SEANP\ EXTERNAL

```

---

### Post by rukiaEnix on 2012-07-19
But maybe would be better if you have all just in one folder, I mean something like this:

```

sudo cp -R /media/314f6070-0529-4b59-8921-d9589883438 /media/SEANP\ EXTERNAL/BACKUPfiles

```

Where BACKUPfiles is a new folder in your external drive

---

### Post by Primefalcon on 2012-07-19
if you really don't care about getting the current install booting again (at last with said user account)


just do a 

sudo chmod -R 777 /media/<driveName>/home/<username>

then you should just be able to copy what files you want using nautilus, no muss, no fuss..

---

### Post by rukiaEnix on 2012-07-19
Now I think about it that was the easiest way... -.-

---

### Post by ilivetowin on 2012-07-19
[rukiaEnix]("http://ubuntuforums.org/member.php?u=835489") and Primefalcon - 

Thank you both very much for taking your time to help out! I copied the command Rukia posted to do the backup, and it is working! The system is going a bit slow, but thats ok. I will be leaving this run overnight(it is over 100 gbs of stuff to transfer) and if come morning it did not work I will try the method you posted Primefalcon. 

Again, I really appreciate both of you taking time out to help! I will post back later tonight or tomorrow and update how it goes! 

Sincerely, 
Sean

---

### Post by rukiaEnix on 2012-07-19
OK! you're welcome!

---

### Post by ilivetowin on 2012-07-21
So the backup method didnt work because one particular file kept having trouble, it kept saying it was invalid or something. But I tried the Chmod 777 method, then went and dragged and dropped my whole home folder onto the backup drive and it worked perfectly. Thank you both so much for your help in this matter! I am so happy to get this taken care of, it has been on my to-do list for a few months and I wasnt sure I would be able to recover my files! 


Sean

---

### Post by rukiaEnix on 2012-07-23
Good to know you solved it with Primerfalcon's help! Please change the thread as solved.

---

