---
title: "Formatting flash drive"
date: 2011-12-20
forum: General Help
---

### Post by meowmix123bbb on 2011-12-20
**Problem**: I just formatted to Ext3 with Gparted on Ubuntu and i can not write anything to the ext3 formatted flash drive. I can only open and see whats in it but not create files onto it.






Please: Post your solutions the easiest way to understand / im a noob at this and just joined seconds ago so please dumb-down everything for me

---

### Post by maverickaddicted on 2011-12-21
Try to change the ownership of the new partition -

```
sudo chown -R USERNAME:USERNAME /media/partition_name
```

replace username with your current user

Frequency out of range is related to resolution, I think. You can google it for more information.

---

### Post by meowmix123bbb on 2011-12-21
> **maverickaddicted said:**
> Try to change the ownership of the new partition -

```
sudo chown -R USERNAME:USERNAME /media/partition_name
```replace username with your current user


I ask for things to be dumb down for me and you slap me with a code then leave ........ do i copy this code and put it to my web address bar ?! and hit enter !!!

---

### Post by QIII on 2011-12-21
Sometimes we geeks have a bad habit of spewing what sounds to us like it is sensible, but it is not to others.  You are well within your "rights" to ask for a better explanation.

It is often best to post one problem at a time in a post.  So it might be best to ask the second (about the monitors) in another post.  That way you spread out your exposure and someone with expertise in one area won't be put off by another question about another subject.

I'm not sure the answer you got about the flash drive is the best solution.  The poster intended for you to complete that instruction in the terminal.  Are you familiar with the terminal?  The reason I say that the answer given may not be the best is that it may be that you want others to be able to use the flash drive.

(By the way, for your future reference, we are all here voluntarily on our own time.  Sometimes people do get started on a solution and then they need to get back to the other business of life.  Be patient.  Someone else will generally come along.  If nobody does in 24 hours, just add a new entry in the thread with the word "bump")

Right at the moment I am typing from my cell phone, so I don't have access to some of my tools and may not be able to help much.  But there are a lot of us hanging around.  Some friendly stranger will be happy to help if you will be reasonably patient.

---

### Post by meowmix123bbb on 2011-12-21
> **QIII said:**
> 
I'm not sure the answer you got about the flash drive is the best solution.  The poster intended for you to complete that instruction in the terminal.  Are you familiar with the terminal?  The reason I say that the answer given may not be the best is that it may be that you want others to be able to use the flash drive.


Yeah i now Terminal , that app on ubuntu its like a black window. I want others and myself to be able to use the ext3 formatted flash drive. I just want to be able to copy something onto the drive but i get an error saying i dont have permission but im running in administrator so i dont get why im getting this error

---

### Post by QIII on 2011-12-21
Do you have files on that drive now?  May I ask why you chose to format it as ext3 as opposed to ext4 or NTFS ("Windows" format)?

---

### Post by meowmix123bbb on 2011-12-21
> **QIII said:**
> Do you have files on that drive now?  May I ask why you chose to format it as ext3 as opposed to ext4 or NTFS ("Windows" format)?


Their is one folder on the drive but i didn't put it there and i want to use ext3 because its recommended for my system for speed and removing video play back problems

---

### Post by QIII on 2011-12-21
I'm not sure how video playback would be less speedy if you used NTFS.  Be that as it may,  if it were formatted as NTFS you probably would be able to just plug it in and move, create and delete files to your heart's content.  As it is now, you will likely need to make entries in a file called fstab in order to mount it.  

It is well past my bed time, so I need to sign off.  If nobody gets back to you in 24 hours, "bump" this thread.

---

### Post by meowmix123bbb on 2011-12-21
> **QIII said:**
>   As it is now, you will likely need to make entries in a file called fstab in order to mount it.  


How do i do that ? 

i just want to copy files to the drive please

---

### Post by QIII on 2011-12-21
Good morning!  I'm on the train to work and using my cell, so I'm a bit limited.  When I get a chance today, I will post a link to a tutorial that should help you get your fstab set up.  Be aware that it may be necessary to have everyone else who uses it do the same thing.  If the colleagues with whom you intend to share files use Windows, this flash drive will NOT work for them unless they have a special Windows application that allows it to communicate with an extx file format.  If you are sharing it with Windows users, I recommend that you copy your files from the flash drive to another locqtion to save them and format the flash drive as NTFS.

---

### Post by meowmix123bbb on 2011-12-21
wait no i dont want to format back to ntfs i want to use ext3 and i cant take out files or put in files because it says i dont have permission. Again, my question is why isn't it letting copy files into it when im the owner running on administrator ?

---

### Post by Rex Bouwense on 2011-12-21
You are only a user who can be granted temporary root access.  Some flash drives are funny and you may have problems with them.  If you can mount the flash drive. right click it and then go to properties.  Once there you should be able to navigate to permissions to change them.

---

### Post by QIII on 2011-12-21
OK.  We'll try the easiest route I can think of right now and see if it works.  I'm not at my Linux machine right now, so this is from memory.

Plug in the flash drive.

Open Nautilus (or whatever your file manager is) in the terminal like this:

```
sudo nautilus
```As super user (which you are now) navigate to the flash drive.  Right click (I think) to pull up the properties dialog.  Under permissions, you should be able to choose permission levels.

Next option is to execute the command suggested by the poster on the previous page, but I don't think that will get you the ability to pass the drive to other users easily.

---

### Post by meowmix123bbb on 2011-12-21
ok i went to terminal typed in sudo nautilus then input my password then right licked my my flahdrive to properties too permissions and i cant click on anything , its all grayed out 


Also , the recovery option is not showing up for me, When restarting my computer i only get a boot ubuntu or Windows vista

---

### Post by maverickaddicted on 2011-12-22
> **meowmix123bbb said:**
> ok i went to terminal typed in sudo nautilus then input my password then right licked my my flahdrive to properties too permissions and i cant click on anything , its all grayed out 


Also , the recovery option is not showing up for me, When restarting my computer i only get a boot ubuntu or Windows vista

Have you tried this command in terminal -

```
sudo chown -R USERNAME:USERNAME /media/partition_name
```

---

