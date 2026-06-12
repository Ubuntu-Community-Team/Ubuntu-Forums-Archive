---
title: "MiniDLNA not serving all files"
date: 2012-05-08
forum: General Help
---

### Post by ozzman2 on 2012-05-08
Hi There

Having some problems with minidlna not serving up all my files.

I opted to install the "[stedy]("https://launchpad.net/%7Estedy6/+archive/stedy-minidna")" version over the flawed "[Oneiric]("https://help.ubuntu.com/community/MiniDLNA")" official version.
#sudo add-repository ppa:stedy6/stedy-minidlna
#sudo apt-get update
#sudo apt-get install minidlna

Edited the config file and made the appropriate changes with directories, etc.
#sudo gedit /etc/minidlna.conf

Problem I am having is that it only serves about 35% of my files to the client (a network capable Onkyo receiver).

I've tried running in debug mode, specifying the configuration file.
#sudo minidlna -d -f /etc/minidlna.conf

That gets it to scan all the files.  I press "Ctrl+C" when it's complete.  Then restart minidlna.
#sudo service minidlna restart

After doing this, 100% of my files appear on my receiver, however, the receiver says "Cannot Play" for 65% of the files (it skips files and will only play those files originally listed prior to the rescan in debug mode).

What makes it really interesting is that if I take any of the files that won't play and stick them on a USB thumb drive (the receiver has a USB port), the files play.  So it wouldn't appear to be a codec problem (all files are FLAC).

Anybody here have any ideas?
Thanks!

---

### Post by cariboo on 2012-05-08
Try:

```
sudo minidlna -R
```

That will scan the library, it usually takes about 5-10 minutes for new titles to appear. Note, cpu levels will be high while scanning the libraries.

---

### Post by ozzman2 on 2012-05-09
Thanks for the quick response.

CPU levels were high for maybe a minute or two.

The results were exactly the same as before.  All files become listed, but still getting "Cannot Play" on the client (for 65% of the library).

Any other suggestions?

---

### Post by ozzman2 on 2012-05-16
Problem solved.  I'll post this here, and maybe it can help someone else.

I completely removed the old "stedy" installation, (repo's, etc).  I think it has issues with Lucid...

Downloaded a tarball from here:
[http://sourceforge.net/projects/minidlna/](http://sourceforge.net/projects/minidlna/)

Extracted contents and simply moved them into the corresponding directories (etc, and usr).  Configured the minidlna.conf file just like before.  Ran a "minidlna -R" like cariboo907 suggested to re-index everything.  Then just ran "minidlna".

All files now show up (and play) on the client.



If any of the Linux guru's out there would like to tell me if I've set myself up for problems in the future by installing minidlna this way, I'd appreciate it.  Thanks.

---

