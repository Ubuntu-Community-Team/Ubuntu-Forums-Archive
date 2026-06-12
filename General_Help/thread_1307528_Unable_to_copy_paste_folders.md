---
title: "Unable to copy paste folders"
date: 2009-10-31
forum: General Help
---

### Post by stef25 on 2009-10-31
I'm trying to copy a folder from usb stick to var/www but Paste is grayed out, I'm unable to create new folders here.

I understand some folders are protected to prevent damage, but this is my localhost folder.

How can I copy files in to here?

---

### Post by scouser73 on 2009-10-31
Go to Terminal and copy & paste this command **> gksudo nautilus**

That will give you root access, you will now be able to copy and paste your folders to the desired location.

---

### Post by unmole on 2009-10-31
Do a 
```
 sudo chown user:user -R /var/www 
```
Replace user with your username.

---

### Post by stef25 on 2009-10-31
Thanks! 

Is the sudo chown command permanent? Ie, I'll always be able to copy paste in this folder, or do I have to do this every time I want to copy something?

---

### Post by DeMus on 2009-10-31
> **stef25 said:**
> Thanks! 

Is the sudo chown command permanent? Ie, I'll always be able to copy paste in this folder, or do I have to do this every time I want to copy something?

Don't use the chown command for system files and folders.
Instead use the tip scouser73 gave you. This is much safer.
Fooling around with ownership can crash your system

---

### Post by stef25 on 2009-10-31
Thanks for the info. Should I undo the chown command to avoid crashing my system in the future?

---

### Post by DeMus on 2009-10-31
> **stef25 said:**
> Thanks for the info. Should I undo the chown command to avoid crashing my system in the future?

I think it is better when you do that. There is a reason why the installation gave certain rights to certain files and folders. Don't mess with them.
I know there are people here on the forum who give answers like unmole did very easily. It's very simple to see through these. You just should be aware of what you are doing.
You have a home folder, this is the only place you own in the whole computer. Here you can save and delete files as you like. All other folders are owned and controlled by root for a reason: safety and stability of the system. Don't mess with that. Or you should like to have to re-install your OS.

---

### Post by stef25 on 2009-10-31
Ok, how can I undo this command and make my system safe again?

---

### Post by SuperSonic4 on 2009-10-31
```
sudo chown root: -R /var/www
``` may work but you may want advice off someone more expert

Note the -R flag means recursive - that is will change the owner of /var/www and all subfolders and files contained therein

---

### Post by DeMus on 2009-10-31
> **stef25 said:**
> Ok, how can I undo this command and make my system safe again?

I would use this:
```
sudo chown root:root -R /var/www
```
It's the same as you used before, only then with your username, now you use root as user and root as group.

---

### Post by stef25 on 2009-10-31
Ok, done. thanks!

---

### Post by DeMus on 2009-10-31
> **stef25 said:**
> Ok, done. thanks!

Please mark this thread as solved so others know with the problem you had there is also a solution in this thread.
Just above your first post in this thread on page 1 there is a text Thread tools. Choose it and then choose "Mark this thread as solved"

Happy Ubuntuing

---

### Post by stef25 on 2009-10-31
Ok done

Not very happy Ubuntuing, struggling hard in fact ...

---

### Post by DeMus on 2009-10-31
> **stef25 said:**
> Ok done

Not very happy Ubuntuing, struggling hard in fact ...

I had several problems with karmic and this morning I re-installed Jaunty which runs fine.
What other problems do you have? Maybe, just maybe, I can help you.

---

### Post by stef25 on 2009-10-31
I need LAMP so I can continue my work abroad, that's the reason I installed it on my machine.

The initial installation via command line went fine, but I don't know how to start Apache or even find where it is located. Searching for "Apache2" bring up alot of results of files located all over the place, but I'm unable to make any sense out of it.

I also need a tool called phpmyadmin which I installed as instructed on the forums, but it fails to work. Already started a thread on it, people helped alot but no luck in the end.

Ubuntu seems very cool on paper but for the work I need to do I can't see it working out, despite the fact you guys are extremely helpful. For every little thing I need to do I have to post on the forums. 

Vista is horrible and too heavy to run on a 5 year old laptop, XP is no longer legally available and Ubuntu is too difficult to get my head around. The only option therefore is a 1500 dollar macbook. Very sad state of affairs.

Sorry Ubuntu.

---

### Post by DeMus on 2009-10-31
> **stef25 said:**
> I need LAMP so I can continue my work abroad, that's the reason I installed it on my machine.

The initial installation via command line went fine, but I don't know how to start Apache or even find where it is located. Searching for "Apache2" bring up alot of results of files located all over the place, but I'm unable to make any sense out of it.

I also need a tool called phpmyadmin which I installed as instructed on the forums, but it fails to work. Already started a thread on it, people helped alot but no luck in the end.

Ubuntu seems very cool on paper but for the work I need to do I can't see it working out, despite the fact you guys are extremely helpful. For every little thing I need to do I have to post on the forums. 

Vista is horrible and too heavy to run on a 5 year old laptop, XP is no longer legally available and Ubuntu is too difficult to get my head around. The only option therefore is a 1500 dollar macbook. Very sad state of affairs.

Sorry Ubuntu.

Can't you open a terminal and type apache? Doesn't that work?
Or type in the terminal which apache
The answer will be a path and filename you have to start.

Or:
For Apache start Synaptic. In the search field type Apache.
You will then get a list of packages related to the Apache webserver.
Right-click on the line which says Apache. From the menu choose properties and click on the TAB Installed files.
Look for a path ending with bin or sbin followed by probably the name apache as filename.
I can not do that right now since I don't have Apache installed.

For phpadmin it will be the same. Try it.

Yes, Linux is not Windows although many people believe it is. It works differently and since everybody is brainwashed with Windows they want to do things the Windows way-which does not work here.
Reading books and internet sites is a good idea. You have to learn to use Linux or the only thing you can do after a year is starting Firefox and browse the net.
Try this for a start:
[ubuntupocketguide]("www.ubuntupocketguide.com")
It's free and easy to read. But there are more, especially sites. Just google a bit.

---

