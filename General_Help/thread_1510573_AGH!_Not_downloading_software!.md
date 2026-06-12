---
title: "AGH! Not downloading software!"
date: 2010-06-15
forum: General Help
---

### Post by unionmaster on 2010-06-15
It is giving me various random errors and not letting me upgrade Ubuntu or download any softwares or anything else of any type, please I need help

---

### Post by howefield on 2010-06-15
The errors are probably not random, but it would help if you posted the first one here.

---

### Post by unionmaster on 2010-06-15
"The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address preferences." 

That is the message it gives me when i check for the updates...

"Could not open 'google-chrome-stable_current_i386.deb'

The package might be corrupted or you are not allowed to open the file. Check the permissions of the file"

That is the error i get when I tried to download a Ubuntu version of Google Chrome, I get that same error with quite a few other things though also, the files aren't corrupted...and I dont know why I wouldn't have the permission to open the file. I got the laptop used from a friend and he said he had it all set but it seems that is not true, I've also had internet problems and am forced to connect by ethernet cord after jumping through many hoops even though he said the wireless care that came with the laptop worked perfectly fine...

---

### Post by ks07 on 2010-06-15
Okay, first thing first... Could you tell us **exactly** how you are trying to install Google chrome?

---

### Post by unionmaster on 2010-06-15
I went to google.com/chrome and selected the 32 bit ubuntu version

---

### Post by ks07 on 2010-06-15
Hmmm... if you're sure the files aren't corrupted, then your next step is to check permissions anyway. Find the .deb file, and right click it. Choose 'properties' and then go to 'permissions'. Check that the owner is set to your username, and make sure that all the boxes either say 'read' or 'read and write'.

---

### Post by unionmaster on 2010-06-15
Ya the owner or whater was set to me and they were all either read-only or read and write and it still said the same error, if you want check the validity of the download of google chrome for ubuntu if you can and see if it is corrupt but its the official download so I dont think thats the case

---

### Post by ks07 on 2010-06-15
Strange. Ok, lets try and do this using the terminal. First of all, move the chrome .deb to the Desktop if it's not there already. (Just to make things simple)

Now, open a terminal (press Alt-f2, and in the box type gnome-terminal and press ok). In the terminal, do the following:

```
cd ~/Desktop && gksudo gdebi-gtk google-chrome-stable_current_i386.deb
```

See what happens, and, if it fails, copy and paste all of the messages that appear in the terminal window here, so we can get some more information.

---

### Post by unionmaster on 2010-06-15
warnings.warn("apt API not stable yet", FutureWarning)


(gdebi-gtk:14981): libglade-WARNING **: Error loading image: Failed to open file '/usr/share/gdebi/gdebi.png': No such file or directory

(gdebi-gtk:14981): libglade-WARNING **: could not convert string to type 'GdkPixbuf' for property 'logo'

---

### Post by howefield on 2010-06-15
> **unionmaster said:**
> The package might be corrupted or you are not allowed to open the file. Check the permissions of the file"

Could be an incomplete download, in fact it is highly likely given your severe connection issues and your updating errors.

Right click the downloaded Chrome .deb package and select properties, what size is it ?

Should be 17.2 MB (18004156 bytes)

---

### Post by ks07 on 2010-06-15
> **unionmaster said:**
> warnings.warn("apt API not stable yet", FutureWarning)


(gdebi-gtk:14981): libglade-WARNING **: Error loading image: Failed to open file '/usr/share/gdebi/gdebi.png': No such file or directory

(gdebi-gtk:14981): libglade-WARNING **: could not convert string to type 'GdkPixbuf' for property 'logo'
:confused: Okay, obviously this goes a lot deeper than my knowledge. From what I can tell, these errors are related to the error you talked about earlier about not finding the repository. I would search around on Google for some of those error messages and look for someone who has had anything similar go wrong.

The only thing I can suggest is trying ```
sudo apt-get update && sudo apt-get upgrade in the terminal
``` and see what errors you get there. If you get the repo problem again, try going to System>Administration>Software Sources and in the 'download from' box choose a different server, then try the above command again. It may fix your problem, or give you a different error that may be less cryptic (such as a broken package).

Anyway, good luck, I've got to run now. I'll check back tomorrow to see how you've done. ):P

---

### Post by unionmaster on 2010-06-15
That was it's exact size...

---

### Post by unionmaster on 2010-06-15
Oksy i did that code and ALOT of stuff came up and my comp isnt letting me paste things into the browser that i didnt get fromt he browser... I was on the usa server and switched to the 'Main Server' and got the repository error, so either way i had a problem.

---

### Post by ks07 on 2010-06-16
Sorry! I don't know if you noticed, but my command was meant to be
```
sudo apt-get update && sudo apt-get upgrade
``` (e.g. no 'in the terminal')

If it gives any specific error messages, try your best and put them on here. As for a real solution, I've drawn up only blanks. Have a look [here]("http://ubuntuforums.org/showpost.php?p=1921742&postcount=8"), and [here]("http://ubuntuforums.org/showthread.php?t=298406"). These guys appear to have had similar error messages to do with their sources.list(s).  One of the threads linked to has a long discussion of a similar problem, so I'd try some of the steps there.

EDIT: Try this in terminal:
```
gksudo nautilus /etc/apt/sources.list.d/
```
Is there anything in this folder? If there is, select it all and cut and paste it to somewhere easy to remember, like your documents, in case this doesn't help. Now, go back to System>Admin>Software Sources and try and change server again. This should search for new packages, but if it doesn't or you want to make sure, in a terminal do ```
sudo apt-get update && sudo apt-get upgrade
``` again. If all goes well, your system should update if it needs to. Then you can again try and install the google chrome package with gdebi as before.

If moving those files doesn't help, cut and paste them back to where they came from using 'gksudo nautilus' again.

---

### Post by unionmaster on 2010-06-17
I didnt have the 'in terminal' in there the first time i got the same REALLY long error, saying multiple things failed...also there was nothing in that folder... >.< Why do i always get stuck with the impossible problems...

---

### Post by Mattevt on 2010-07-07
I just had this same problem. If it's any help to any one, instead of installing the .deb right away, I saved it to my computer and double-clicked it from there and everything was fine.

---

### Post by jerm1027 on 2012-01-09
Ok, so more than a year later, I'm still having the same problem. I initially tried this with the 64 bit version, but then I realized I wasn't running 64 bit ubuntu. ](*,)

So I double checked ```
 jeremy@jeremy-AO722:~/Downloads$ uname -i
i386

```I then downloaded the 32bit version of Chrome

After that, here is what I did
```

jeremy@jeremy-AO722:~/Downloads$ gdebi google-chrome-stable_current_i386.deb
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Building data structures... Done 
Failed to open the software package
The package might be corrupted or you are not allowed to open the file. Check the permissions of the file.
jeremy@jeremy-AO722:~/Downloads$ chmod 777 google-chrome-stable_current_i386.deb 
jeremy@jeremy-AO722:~/Downloads$ gdebi google-chrome-stable_current_i386.deb
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Building data structures... Done 
Failed to open the software package
The package might be corrupted or you are not allowed to open the file. Check the permissions of the file.
jeremy@jeremy-AO722:~/Downloads$ sudo gdebi google-chrome-stable_current_i386.deb
[sudo] password for jeremy: 
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Building data structures... Done 
Failed to open the software package
The package might be corrupted or you are not allowed to open the file. Check the permissions of the file.

```Can anyone tell me what's wrong or offer suggestions?

UPDATE:
I actually downloaded the file twice to confirm data integrity, and both files are identical at 27.9MB each. I wish Google posted the MD5 sum just so I can absolutely rule out data corruption.

---

### Post by overdrank on 2012-01-09
Please start a new thread with your issues. Thread closed.

---

