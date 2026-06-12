---
title: "ok what the heck did i do???? helppppp"
date: 2011-06-09
forum: General Help
---

### Post by gene simmons on 2011-06-09
ok ill try and keep this short,i downleaded remasterz as i wanted to make a copy of my distro and all the changes i have made to it,remasterz got an error when i was loading it thru spftware centre but it loaded anyways,i clicked on make a distro to share with freinds and it started and took awhile so i jumped in the shower and when i got out i had a error page saying i had only 1 gig of hardrive space left,i had 23 beofre i started,anyhways remasterz sttoped working as i had m more hardrive space left,it was only 37% done and alreadt ate up 22 gigs of stuff,i went to the file in home called remasterz and delited it to thetrash,i use bleachbit so i ran that to clean the trash butis didnt clean my sytem,i still have only 1 gig of space left and now i cant find the file i delated to try and get rid of it,where did the 22 gigs go and how can i fix this prob,also when i get back up and running whats a good program to make a live dvd of my changes,i want to try another distro and if i want to come back to ubuntu i hope i dont have to load all my changes again,thanx for reading

---

### Post by linuxinstalledfromhdd on 2011-06-09
You need to update it from the repository. 

Here is a guide:

[http://cinderbox.net/2011/06/02/creating-custom-ubuntu-live-usb-with-remastersys/](http://cinderbox.net/2011/06/02/creating-custom-ubuntu-live-usb-with-remastersys/)

First completely uninstall it from within Synaptic Package Manager (right click and select "completely remove")

Reinstall it with the instructions in the link provided above...

---

### Post by wildmanne39 on 2011-06-10
> **gene simmons said:**
> ok ill try and keep this short,i downleaded remasterz as i wanted to make a copy of my distro and all the changes i have made to it,remasterz got an error when i was loading it thru spftware centre but it loaded anyways,i clicked on make a distro to share with freinds and it started and took awhile so i jumped in the shower and when i got out i had a error page saying i had only 1 gig of hardrive space left,i had 23 beofre i started,anyhways remasterz sttoped working as i had m more hardrive space left,it was only 37% done and alreadt ate up 22 gigs of stuff,i went to the file in home called remasterz and delited it to thetrash,i use bleachbit so i ran that to clean the trash butis didnt clean my sytem,i still have only 1 gig of space left and now i cant find the file i delated to try and get rid of it,where did the 22 gigs go and how can i fix this prob,also when i get back up and running whats a good program to make a live dvd of my changes,i want to try another distro and if i want to come back to ubuntu i hope i dont have to load all my changes again,thanx for reading
Hi, if removing it completely by synaptic does not work, run this command in a terminal to get rid of it completely.
```
sudo apt-get --purge remove packagename
```

---

### Post by gene simmons on 2011-06-10
ok i did both of those sgestions and i believe the program is totally unintalled but the file that took my 22gigs is still missing,i tried deleting the file to the trash before uinstalling the program and now the program is unistalled but the file is still some where,my system is only showing 1 gig of space left,how can i find the 22 gig file and restore my system,thanx for the sugestions so far

---

### Post by jtarin on 2011-06-10
> **gene simmons said:**
> ok i did both of those sgestions and i believe the program is totally unintalled but the file that took my 22gigs is still missing,i tried deleting the file to the trash before uinstalling the program and now the program is unistalled but the file is still some where,my system is only showing 1 gig of space left,how can i find the 22 gig file and restore my system,thanx for the sugestions so far
Did you look in /temp?
[Finding large files.]("http://www.cyberciti.biz/faq/find-large-files-linux/")

---

### Post by gene simmons on 2011-06-10
damn i checked temp and its not in there either,i hope i can find it,i only have less than 1 gig available now,i need to find that 22 gigs,any more sugestions guys

---

### Post by phillroberts on 2011-06-10
Try using the find command.  If it's one file (e.g. an ISO), find should help. 

```
> find / -size +5G
```

The above says to start searching from the root and find any files greater than 5 gigs.  Adjust the number as you see fit to find the file.

---

### Post by gene simmons on 2011-06-10
thxn for the reply,i tried your sugestion and got this reply,

dave@ubuntu:~$ > find / -size +20g
bash: /: Is a directory
dave@ubuntu:~$ > find / -size +5G
bash: /: Is a directory
dave@ubuntu:~$ 

am i typing somthing wrong,again thanx for the tips so far

---

### Post by wildmanne39 on 2011-06-10
> **gene simmons said:**
> thxn for the reply,i tried your sugestion and got this reply,

dave@ubuntu:~$ > find / -size +20g
bash: /: Is a directory
dave@ubuntu:~$ > find / -size +5G
bash: /: Is a directory
dave@ubuntu:~$ 

am i typing somthing wrong,again thanx for the tips so far
Hi, you say you deleted it to the trash bin did you empty the trash?

---

### Post by jtarin on 2011-06-10
Try ```
sudo  find / -size +5G
```

---

### Post by hawthornso23 on 2011-06-10
Don't put the > in there. That is just supposed to be the command prompt.

```
sudo find / -size +5G

```

---

### Post by gene simmons on 2011-06-10
thanx so much guys,i should have cought that point,i found the file and its in root trash,how do i delete files in root trash,heres a shot of where it is

dave@ubuntu:~$ sudo  find / -size +5G
[sudo] password for dave: 
find: `/proc/9742/task/9742/fd/5': No such file or directory
find: `/proc/9742/task/9742/fdinfo/5': No such file or directory
find: `/proc/9742/fd/5': No such file or directory
find: `/proc/9742/fdinfo/5': No such file or directory
/host/ubuntu/disks/root.disk
find: `/home/dave/.gvfs': Permission denied
/root/.local/share/Trash/files/remastersys/remastersys/ISOTMP/casper/filesystem.squashfs
dave@ubuntu:~$

---

### Post by jtarin on 2011-06-10
Only include the commands after the prompts:```
su root
``` will get you to a root prompt like this ```
root@godzilla:/home/username#
```then ```
cd
```will get you a prompt like this ```
root@godzilla:~#
```Now ```
root@godzilla:~#cd .local/share/Trash 
``````
root@godzilla:~/.local/share/Trash# rm -r files
``````
root@godzilla:~/.local[/email]/share/Trash# rm -r info
``````
root@godzilla:~/.local/share/Trash# mkdir files
``````
root@godzilla:~/.local/share/Trash# mkdir info
```now to get back to your user```
su username
```then```
cd
```

---

### Post by linuxinstalledfromhdd on 2011-06-10
> **gene simmons said:**
> ok i did both of those sgestions and i believe the program is totally unintalled but the file that took my 22gigs is still missing,i tried deleting the file to the trash before uinstalling the program and now the program is unistalled but the file is still some where,my system is only showing 1 gig of space left,how can i find the 22 gig file and restore my system,thanx for the sugestions so far

Try using bleachbit to see if you can't get that space back:

sudo apt-get install bleachbit
sudo bleachbit

Be careful as to not delete your bookmarks or passwords.

Make sure if you are going to reinstall Remastersys that you do so from the Remastersys Repo like this:

[http://cinderbox.net/2011/06/02/creating-custom-ubuntu-live-usb-with-remastersys/](http://cinderbox.net/2011/06/02/creating-custom-ubuntu-live-usb-with-remastersys/)

After you get that installed you might want to make sure to click "Clean" to make sure any residual files from your previous installation are successfully removed before you try to create another ISO. :)

---

### Post by jtarin on 2011-06-10
> **linuxinstalledfromhdd said:**
> 
After you get that installed you might want to make sure to click "Clean" to make sure any residual files from your previous installation are successfully removed before you try to create another ISO. :)+1 to that...I would have suggested that earlier but saw that the OP deleted everything.:p

---

### Post by gene simmons on 2011-06-10
awsooome,thanx so much guys for all your help.i have my space back,all seems well again.this is solved thanx again.  gooooo canuuks yaaaa

---

### Post by jtarin on 2011-06-11
Please mark this thread as solved. It could help someone else.

---

