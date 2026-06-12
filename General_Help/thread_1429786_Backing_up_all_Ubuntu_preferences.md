---
title: "Backing up all Ubuntu preferences?"
date: 2010-03-14
forum: General Help
---

### Post by opethfan89 on 2010-03-14
Hi all

I'm needing to wipe out my computer, but my only hesitation is that I've made so many awesome changes to my Ubuntu install and I don't want to lose them, since alot of it was copying/pasting terminal commands or following instructions from blogs that I didn't bookmark.  Is there any way I'd be able to backup all my preferences, i.e. installed drivers, desktop configuration, basically all the little things?

Thanks for any replies, any help is appreciated.

Opethfan89

---

### Post by oldfred on 2010-03-14
This post discusses backup and therefore what is important.

Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)

Your user settings are in /home which you may want to move to a separate partition before reinstalling.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

I like to also backup my applications and occasionally export this so it is in my backups:
sudo cp /etc/apt/sources.list ~/sources.list.backup

dpkg --get-selections | grep -v deinstall > ubuntu-files
or
dpkg --get-selections > ubuntu-files

If you have make major system changes they should be in /etc which you may also want to backup. I try to keep track of one's I have manually edited as I sometimes need them, but also found new installs often conflict with old settings.

Depending on how old your commands are you can list history - 'history' in terminal. My clean install of Karmic I listed my history to save it for my next install so I do not have to look up various documents I have saved on things I want to modify or add. Next time I will convert my history to a bash file(s) to semi-automate the process.

---

### Post by dcstar on 2010-03-14
> **oldfred said:**
> 
........
dpkg --get-selections | grep -v deinstall > ubuntu-files
or
dpkg --get-selections > ubuntu-files
........

There is no need whatsoever to use the command line when the "Save Markings" feature in Synaptic will do the job.

---

### Post by opethfan89 on 2010-03-14
Thanks guys, I will go through and follow all these steps when I get a little bit more time later in the week...In the meantime, just gonna keep using Ubuntu since Windows decided to crap out...

Thanks again

---

### Post by opethfan89 on 2010-03-18
Ok I used the psychocats tutorial and it seems they actually have a section devoted TO backing up Ubuntu, so I used the

rsync -av

command to back up my /user/home directory. I am wiping out at the moment so the question arises, **what do I DO with my backup once I boot back into Ubuntu?** that is, how do I restore my files? and will all my settings go back to normal?

---

### Post by oldfred on 2010-03-18
They also have a section on moving home.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

Often the permissions and ownership get messed up and the link to dmrc discusses the correct settings for  /home once you have copied all the data back.

---

### Post by opethfan89 on 2010-03-21
> **oldfred said:**
> They also have a section on moving home.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

Often the permissions and ownership get messed up and the link to dmrc discusses the correct settings for  /home once you have copied all the data back.

I did read that section and plan to do so on my next install, but that doesn't answer how I can restore the /home folder that I spent time backing up?

---

