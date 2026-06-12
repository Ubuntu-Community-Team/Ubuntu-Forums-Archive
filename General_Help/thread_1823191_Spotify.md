---
title: "Spotify"
date: 2011-08-11
forum: General Help
---

### Post by -OXEN- on 2011-08-11
Im new in the linux community and i ask for help.
I want to install spotify on Ubuntu 11.XX. But I dont know how.
[http://www.spotify.com/se/download/previews/](http://www.spotify.com/se/download/previews/) (Instructions)
Can someone please help me installing this program?
/-OXEN-

---

### Post by Vaphell on 2011-08-11
add repository to sources recognized by the system
```
sudo sh -c 'echo "deb http://repository.spotify.com stable non-free" >> /etc/apt/sources.list'
```

configure authorization
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4E9CFF4E
```

refresh info about repositories and available packages
```
sudo apt-get update
```

install spotify packages
```
sudo apt-get install spotify-client-qt spotify-client-gnome-support
```

simply highlight commands here and middleclick-paste them in order into terminal window.

---

### Post by flipper T on 2011-08-11
the version of spotify described above is native to linux but will only work if you have a paid for spotify account

if you use the free version, you can download the windows version of spotify & run it using WINE.

it runs fine.

---

### Post by Milbos on 2011-08-24
Just recently moved to Ubuntu after my sllooooooow windows recked my laptop. 

anyway, I've been trying to get spotify running, having no idea what the difference between the command and terminal windows are. 

I figured out from the instructions above, but just wanted to ask, should understand lines that I'm copying into the terminal, or can I just trust posts like this? don't want to accidently do something to mess my system up. 

regardless - this was so simple to get spotify working and integrated!!

thanks!!

---

### Post by flipper T on 2011-08-24
read this:

[http://ubuntuforums.org/announcement.php?f=331](http://ubuntuforums.org/announcement.php?f=331)


never had a problem myself

---

### Post by Milbos on 2011-08-24
nice thanks, I need to get learning this stuff, absolute beginner... I'll begin by trying to understand the above code I just fed in!!!

---

### Post by CJ_Hudson on 2011-08-25
Please, I have been trying for a couple of days to get Spotify working in Linux with wine, but as it is finishing downloading it there is an error and it won't install properly or run and there is no icon:(. What am I doing wrong? I have got other apps working fine in Wine.

The error message is 

Checksum for /home/chris/.cache/winetricks/spotify/SpotifyInstaller.exe did not match, retrying download

?

Ah, 's okay, found instrs here: [http://www.spotify.com/uk/help/faq/wine/](http://www.spotify.com/uk/help/faq/wine/)

Cool.

Edit: This actually worked fine. For a while.

---

### Post by CJ_Hudson on 2011-09-25
My version of Spotify seems completely corrupted.
Try to share a track to facebook and get error. 
Now it wouldn't even let me play a track and crashes.
Will try re-installing and not deleting the second icon it puts on the desktop.
Will try to get error messages in Wine an post them here.
Tries uninstalling ti and re-installing it but couldn't get any instructions to uninstall it and when I 're'-installed it same problem.
The only thing that had changed on my computer was I had transferred some photos from my Blackberry onto the hard drive. Can't think why this should've corrupted Spotify though?
PLEASE ANYONE HELP!!!!!! I'M DESPERATE. (-:

Edit: Had to disable Facebook app and works fine now!

---

### Post by CJ_Hudson on 2011-09-29
Bump

---

### Post by CJ_Hudson on 2011-10-02
Bump.

By the way, **Mr. Moderator**, I can't seem to change my profile picture. Is there a reason for this?

---

### Post by mikaela89 on 2011-12-31
> **Vaphell said:**
> add repository to sources recognized by the system
```
sudo sh -c 'echo "deb http://repository.spotify.com stable non-free" >> /etc/apt/sources.list'
```configure authorization
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4E9CFF4E
```refresh info about repositories and available packages
```
sudo apt-get update
```install spotify packages
```
sudo apt-get install spotify-client-qt spotify-client-gnome-support
```simply highlight commands here and middleclick-paste them in order into terminal window.


Hej! 
Just tried pasting all that in the terminal but it's not working, says it contains broken packages and something about having an unstable distribution. 
I have also serious problem with my spotify, currently running it through wine but it usually just freeze in the middle of a song and just closes itself constantly. Anyone who know about this problem?
Is the easiest thing just to download it again and instal it through wine?

---

### Post by Derek Karpinski on 2011-12-31
> **mikaela89 said:**
> Hej! 
Just tried pasting all that in the terminal but it's not working, says it contains broken packages and something about having an unstable distribution. 
I have also serious problem with my spotify, currently running it through wine but it usually just freeze in the middle of a song and just closes itself constantly. Anyone who know about this problem?
Is the easiest thing just to download it again and instal it through wine?

Change the last step to:

```
sudo apt-get install spotify-client-qt
```For some reason, 
spotify-client-gnome-support won't install, and it seems to work fine without it.

---

### Post by Mat11 on 2011-12-31
> **MogBug said:**
> Bump.

By the way, **Mr. Moderator**, I can't seem to change my profile picture. Is there a reason for this?

i

---

