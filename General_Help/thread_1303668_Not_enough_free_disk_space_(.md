---
title: "Not enough free disk space :("
date: 2009-10-28
forum: General Help
---

### Post by supervillain on 2009-10-28
I keep getting an error message when I try to run the Update Manager.  It says this...


Not enough free disk space

The upgrade needs a total of 483M free space on disk '/'. Please free at least an additional 483M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.


I am new to linux and I am using ubuntu 9.04.  I have about 200GB of free disk space but it does not look like the update manager is pointing to the hard drive I want to use.  Any ideas on a fix for this?  thanks so much.

---

### Post by Giblet5 on 2009-10-28
Try to eat 1000 hamburgers: why did you stop before you were done? Yes, exactly! Same thing here.

It doesn't make any difference how big your disk drive is. If it's full, then it's full. That's true on Ubuntu, Windows, Mac, DOS, CPM, MVS...

Open a terminal window, execute this command, and post the output: ```
df
```

---

### Post by drs305 on 2009-10-28
supervillain,

Welcome to Ubuntu. There is a very good chance you are victim of a "bug" in the Ubuntu installer. I write frequently on this issue, as recently as yesterday (see below).

If the results of the "df -h" command produce results showing a partition of 2.5GB, refer to this post - especially if you just installed Ubuntu with a "side-by-side" option with Windows:

[http://ubuntuforums.org/showthread.php?t=1302903#5]("http://ubuntuforums.org/showthread.php?t=1302903#5")  Post number 5.

---

### Post by supervillain on 2009-10-28
thnaks for the swift replys guys.  I ran the commands and posted the results below.  drs305, i see a 2.3GB partition but not a 2.5.  also, i DID install side-by-side with windows 7 ultimate  :(

I am sure it is not full because when I load windows 7 I have 173GB free.


```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda6              2403388   2338884         0 100% /
tmpfs                  1547780         0   1547780   0% /lib/init/rw
varrun                 1547780        84   1547696   1% /var/run
varlock                1547780         0   1547780   0% /var/lock
udev                   1547780       176   1547604   1% /dev
tmpfs                  1547780       476   1547304   1% /dev/shm
lrm                    1547780      2392   1545388   1% /lib/modules/2.6.28-11-generic/volatile
overflow                  1024        16      1008   2% /tmp

ryan@ryan-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             2.3G  2.3G     0 100% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G   92K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  176K  1.5G   1% /dev
tmpfs                 1.5G  476K  1.5G   1% /dev/shm
lrm                   1.5G  2.4M  1.5G   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M   16K 1008K   2% /tmp
```

---

### Post by drs305 on 2009-10-28
> **supervillain said:**
> thnaks for the swift replys guys.  I ran the commands and posted the results below.  drs305, i see a 2.3GB partition but not a 2.5.  also, i DID install side-by-side with windows 7 ultimate  :(

I am sure it is not full because when I load windows 7 I have 173GB free.


```


ryan@ryan-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
**[COLOR="Red"]/dev/sda6             2.3G  2.3G     0 100% /[/COLOR]**
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw

```


Sometimes it's 2.3GB, sometimes it's 2.5, but either way sad to say you are a victim of the bug. You will have to either reinstall and move the slider in Step 4 or resize your Ubuntu partition, taking space from Windows or another partition.  You had lots of free space, but Ubuntu took only 2.3GB of it, which unfortunately isn't large enough to support a normal installation.

Both would probably take about the same amount of time.

Refer to the link in my previous post.

---

### Post by Anonymousable on 2009-10-28
You have Win7 installed on a seperate partition. The linux partition is full, as you can see by the "100%" in the first row.

Try running sudo apt-get clean from a terminal (Applications>Accessories>Terminal), that should free some space. If it still gives you the same error, you'll have to delete some files or move them onto the windows partition.

---

### Post by Giblet5 on 2009-10-28
> **drs305 said:**
> Sometimes it's 2.3GB, sometimes it's 2.5, but either way sad to say you are a victim of the bug. You will have to either reinstall and move the slider in Step 4 or resize your Ubuntu partition, taking space from Windows or another partition.  You had lots of free space, but Ubuntu took only 2.3GB of it, which unfortunately isn't large enough to support a normal installation.

Both would probably take about the same amount of time.

Refer to the link in my previous post.


Nice call! Has this been officially reported as a bug yet?

---

### Post by drs305 on 2009-10-28
> **Giblet5 said:**
> Nice call! Has this been officially reported as a bug yet?

It has. I reported it in July, then another forumite really pressed the issue in late August. I don't have the link handy.

The result was that it was finally fixed in Karmic and shouldn't be an issue in the release tomorrow. I believe what they did was just change the default to produce a viable partition size instead of the old default of 2.3Gb. I don't know if they redesigned the page to make it more apparent that the user should/could use the slider bar at the bottom of the page to change the size.

Unfortunately in my mind, the devs decided not to go back and change it it earlier releases. It would involve making an entirely new ISO version and I guess they were opposed to doing that. The decision means that from time to time new users will be exposed to the 'bug' as long as they try to install Jaunty from the current ISOs. It happens often enough that I wrote the two tutorials on how to "recover" from such an installation.

The good news is that soon most new users should be deciding on either Hardy for LTS or Karmic for a more up-to-date release.

---

### Post by Giblet5 on 2009-10-28
Thanks. I was concerned that it would release tomorrow, forcing me to spend the next week ..... elsewhere.

---

### Post by supervillain on 2009-10-28
drs305,  thanks for the info.  Your tutorial looks very helpful but it seems a little difficult for my linux skills.  I am going to go with the reinstall since it only took about 10 mins on my computer.  Quickly,  how do I delete 9.04 and reinstall?  I don't see an option for that anywhere.  Thanks again everyone.  You have been extremely helpful.

---

### Post by drs305 on 2009-10-28
> **supervillain said:**
> drs305,  thanks for the info.  Your tutorial looks very helpful but it seems a little difficult for my linux skills.  I am going to go with the reinstall since it only took about 10 mins on my computer.  Quickly,  how do I delete 9.04 and reinstall?  I don't see an option for that anywhere.  Thanks again everyone.  You have been extremely helpful.

You would just start the installation over from the livecd. In Step 4, if asked, select the / partition and tick the "format" option. That will overwrite what's on the partition now. The side-by-side option may not ask about that - if it doesn't, it's just going to overwrite it anyway. If given the option, format any partition it wants to install on THAT IS NOT WINDOWS. And don't forget to move the slider. At least 10GB or more should be a comfortable minimum size for the / partition, excluding any data files you plan on storing on that partition.

---

