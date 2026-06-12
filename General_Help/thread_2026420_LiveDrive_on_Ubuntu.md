---
title: "LiveDrive on Ubuntu?"
date: 2012-07-15
forum: General Help
---

### Post by GaryReggae on 2012-07-15
Not sure if this is the best place to post this so please let me know if not.

Yesterday, I (perhaps foolishly) purchased a five-year subscription to 'KnowHow Cloud Services'; basically, it's a cloud for backing up data or storing it there. It is powered by LiveDrive.

It says I can back up three computers and I've got my Windows machine backed up fine. However, most of my data is on my server, which runs on Ubuntu.

On Windows, you can install an app that does the syncing thing but that's just for Windows. Does anyone here have experience of using LiveDrive on a Linux machine? If not then I guess the only option is to rebuild the server with Windows and I really would rather not have to resort to that!

I'm posting this here rather than on the LiveDrive forum as I assume I'll get the glib response of "We don't support Linux".

---

### Post by codemaniac on 2012-07-15
Hi GaryReggae,


Cannot you just setup SFTP to access your liveDrive account from Ubuntu .
Like below .

[http://blog.livedrive.com/2011/06/for-advanced-users-accessing-your-livedrive-pro-suite-account-from-linux/](http://blog.livedrive.com/2011/06/for-advanced-users-accessing-your-livedrive-pro-suite-account-from-linux/)

---

### Post by GaryReggae on 2012-07-15
Thanks - but unfortunately, the interface is different on the version of Ubuntu I have (12.04; I much prefer the previous versions' interface as I can't find anything on this one).

I have managed to find 'Connect to server' but the dialogue box that comes up looks like the attachment. I've tried OKing that with the suggested FTP address but it comes up with a 'permission denied' message – odd as it never even got as far as asking for a username or password.

---

### Post by codemaniac on 2012-07-15
What happens when you sftp from a commandline to connect to the mentioned liveDrive address ?

There is also sftp clients like FileZilla , I dont know if it will for you to set up your LiveDrive account .

In order to be sure you are using the correct ftp address you can call up the support .

---

### Post by GaryReggae on 2012-07-15
> **codemaniac said:**
> What happens when you sftp from a commandline to connect to the mentioned liveDrive address ?

There is also sftp clients like FileZilla , I dont know if it will for you to set up your LiveDrive account .

In order to be sure you are using the correct ftp address you can call up the support .

Thank you! I thought I'd give Filezilla a go and that works a treat! :D

---

