---
title: "virus? exe file everywhere"
date: 2010-06-23
forum: General Help
---

### Post by beningh on 2010-06-23
In all of my folders I got a .exe file named after the folder it is in. So far CLAMTK has found 717 of them and it still got 75% to go. Each file is 260k in size. When I open GIMP it hangs up when it installs plug-in files. It shows that it is trying to load "plug-in.exe". Then I saw that the SYSTEM MONITOR/PROCESSES had "plug-in.exe" using 50%. What are they and how did I get it?  Thanks   :-k

---

### Post by Rubi1200 on 2010-06-23
Is this a Wubi install of Ubuntu?

Are you running GIMP in Wine with root privileges?

You really need to give us more information please so we can help you.

---

### Post by beningh on 2010-06-23
Thanks.  No. It is a standard installation Ubuntu 10.4. No M/S windows. No Wubi.  I use wine for photomatix. My GIMP is Linux.
  Clamtk virus now has 1380 viruses found with 65% more to check on the drive.  The exe files are under my home folder, not the system files.

---

### Post by Smart Viking on 2010-06-23
Hm, that sounds like some wine application went terrible wrong, or a virus in wine or something.

You could try to install a virus program and scan the harddrive. :)

---

### Post by Rubi1200 on 2010-06-23
plugin.exe seems to be a known Windows virus and although Clamtk is known for a high rate of false positives, this sounds very strange.

If you are able it might be worthwhile downloading and burning to disc the following:

[http://www.raymond.cc/blog/archives/2008/12/11/13-antivirus-rescue-cds-software-compared-in-search-for-the-best-rescue-disk/](http://www.raymond.cc/blog/archives/2008/12/11/13-antivirus-rescue-cds-software-compared-in-search-for-the-best-rescue-disk/)

Then boot up and let them do their work.

I mean, pick one and use it as a LiveCD. I am really not convinced that installing an antivirus program on Ubuntu is that effective.

from bodhi.zazen's security sticky:

> Discussions about running Windows viruses on wine crop up from time to time and it is possible to run some Windows viruses on wine.

See these links :
[LIST]
[*][McAfee Avert Labs Blog]("http://www.avertlabs.com/research/blog/index.php/2009/02/23/running-windows-malware-in-linux/")
[*][Running Windows viruses in wine]("http://www.linux.com/articles/42031")
[/LIST]

So what do you need to know about Windows viruses if you want to run wine?

1. First, the "golden rule" : [COLOR=darkred]**DO NOT RUN WINE AS ROOT**[/COLOR]. If you are **NOT** running wine as root then wine will not have the necessary permissions to affect system files.

2. So, if you are running wine as a user, a Windows virus will be confined to your home directory.

3. You can further confine the "fake c drive" located at ~/.wine if you remove any symbolic links outside ~/.wine. With a default installation there is link with a default installation / configuration of wine :
[LIST]
[*]~/.wine/dosdevices/z: -> links to /
[/LIST]

A link from ~/.wine/dosdevices to the root directory ( / ) should concern you for obvious reasons.

You can remove it with :

 	Code:
 	unlink ~/.wine/dosdevices/z: 
Do not worry, that command will not affect wine at all, I run it all the time :twisted:

You may need to make a link in ~/.wine/dosdevices to your cdrom and/or you may be tempted to link to your home directory, but I advise against keeping using these links (beyond the time needed for actually installing applications).

I advise against any links to removable devices (it should not be *that* difficult to copy files needed to the appropriate location in ~/.wine/drive_c ).

4. Consider running an antivirus program and scanning ~/.wine and any removable devices or other locations you use outside of ~/.wine to store programs or data to be used with wine. Scan any data / applications you use with Windows.

5. Consider confining wine with Apparmor. 

6. Be sure to file a bug report with the wine project as they have a very active security team (it is unrealistic, however, to expect the wine team to be able to protect you from all Windows viruses all the time). [Wine Bug Reports]("http://bugs.winehq.org/")

7. Take the same precautions with wine as you would with Windows. Do not install untrusted applications from untrusted sources.

If you follow the above advice, Windows viruses will be confined to ~/.wine and they do not have permission to change system files. This means to remove them you simply:

 	Code:
 	rm -rf ~/.wine 
[COLOR=darkred]Please take care, this command deletes everything in your wine directory including all data and all applications.[/COLOR]

You then need to restore your wine directory from a known good backup (you do keep backups ?).

Update: so Photomatix uses plugins apparently. I must stress here that running Wine as root is considered to be potentially extremely dangerous.

---

### Post by beningh on 2010-06-23
Thanks.  Photomatix does not use plug-ins. GIMP does.  This was the way I found the first exe files. "plug-in.exe" is under the ".gimp-2.6/plug-in" folder. Each folder has this exe file, but named after the folder it is in. "music.exe" is in folder music. "videos.exe" is in folder video. They are all like that. Each is 261k long with the date 23 july 2009.  Clamtk visur checker how has found 4926 files, with 14% left to scan.

---

### Post by Smart Viking on 2010-06-23
Thats horrible. :O

What is the variable to current folder?
Maybe it could be possible to make a script that removes everyfile that starts with the folder variable and ends with *exe, but i don't know if that would kill the virus though, maybe it would just spread again.

---

### Post by wojox on 2010-06-23
[Plugin-exe virus]("http://comprolive.com/remove/harmful/exe/plugin-exe")

Can you just delete them?

I don't think linux knows what to do with ac .exe file

---

### Post by lisati on 2010-06-23
You might want to reconfigure Wine so that it doesn't map a drive to /.

---

### Post by beningh on 2010-06-23
The scan has finished. It says I got 5183 "worm.Autorun-1782", "no action taken. It will only let me delete one file at a time.

---

### Post by Rubi1200 on 2010-06-23
[http://www.pc1news.com/virus/alias-worm-autorun-1782-51366.html](http://www.pc1news.com/virus/alias-worm-autorun-1782-51366.html)

---

### Post by wilee-nilee on 2010-06-23
> **Rubi1200 said:**
> [http://www.pc1news.com/virus/alias-worm-autorun-1782-51366.html](http://www.pc1news.com/virus/alias-worm-autorun-1782-51366.html)

Your link is considered unsatisfactory by wot look at the round yellow icon.
[ATTACH]161318[/ATTACH]

I would not run a unsatisfactory scanner, wot is a pretty good indicator.

Thread starter If you have that many hits reinstall. Even if you think you have it fixed if anything has gotten to root there will probably be rootkits at best, some of which can't even be detected.

---

### Post by Rubi1200 on 2010-06-23
> **wilee-nilee said:**
> Your link is considered unsatisfactory by wot look at the round yellow icon.
[ATTACH]161318[/ATTACH]

I would not run a unsatisfactory scanner, wot is a pretty good indicator.

Thread starter If you have that many hits reinstall. Even if you think you have it fixed if anything has gotten to root there will probably be rootkits at best, some of which can't even be detected.

Thanks for pointing this out wilee-nilee. I don't use WOT; therefore, could not have known.

I agree that reinstalling may be the only safe option.

Just to be clear, I posted the link for the information it contained thinking it might help.

> **Worm.Autorun-1782 has been detected in these files:**

                                          If you have the following files on your system with the corresponding md5's                     you are most likely infected.  You can remove Worm.Autorun-1782 by deleting the files.                     

Of course,

> Even if you think you have it fixed if anything has gotten to root there will probably be rootkits at best, some of which can't even be detected

---

### Post by nerdy_kid on 2010-06-23
and now we have viruses on linux :-({|=

i wouldnt touch your root account during all this btw.  I would also go the script method to delete all the files, I am a sucky (like accentually destroy all your files) script writer or I would write one for you.  I would also delete ~/.wine.
but whatever you do, DONT sudo ANYTHING cause then you will be reinstalling.

also you could do these.
this will automaticly remove all infected files.  could be dangerous.
```

clamscan -r -i --remove=yes ~/

```
if you are more comfortable moving the files instead, make a folder that you are going to move them into and then
```

clamscan -r -i --move=FOLDER ~/

```

---

### Post by nerdy_kid on 2010-06-23
how would a virus be able to install a rootkit without sudo privileges?

---

### Post by StuartN on 2010-06-23
If there is a file with the same name as its parent directory, the following will locate it, and you could replace **echo $dir** with  **rm -i "$dir/$(basename $dir)**" or similar:

```
for dir in $(find Videos -type d) ; do
  if [ -f "$dir/$(basename $dir)" ] ; then
    echo $dir
  fi
done
```

Alternatively, if all the .exe files are the same, then **fdupes** has the option to delete all the duplicates in one go.

It might be worth doing **head something.exe > signature**, or saving one copy, to do a final check for files with the same or similar first few bytes.

---

### Post by wilee-nilee on 2010-06-23
> **nerdy_kid said:**
> how would a virus be able to install a rootkit without sudo privileges?

With that many hits we don't know what has happened, better safe then sorry. Clamtk will give false positives but that many, along with .exe files attached to everything I would have stopped the scan and deleted the whole thing immediately myself, but I would have never gotten there anyway.

I would never use wine myself I have windows anyway.

---

### Post by 3Miro on 2010-06-23
Yesterday I was installing a wine game and I types setup.exe without putting wine before it. The installer ran, which means that Linux can run windows programs just by typing a name.

Uninstall wine, this will stop the spread of the virus. Then delete all the infected files and probably .wine just to be safe. Also check to see if there is /root/.wine folder and delete that one as well. This should fix the problem.

After you have cleared all instances of the virus, you can install wine back.

---

### Post by nerdy_kid on 2010-06-23
> **3Miro said:**
> Yesterday I was installing a wine game and I types setup.exe without putting wine before it. The installer ran, which means that Linux can run windows programs just by typing a name.

Uninstall wine, this will stop the spread of the virus. Then delete all the infected files and probably .wine just to be safe. Also check to see if there is /root/.wine folder and delete that one as well. This should fix the problem.

After you have cleared all instances of the virus, you can install wine back.

he cant uninstall wine with out running sudo, running sudo would be plain stupid at this point.  However, by booting of a liveCD, mounting the infected system's root partition and removing executible permissions from /usr/bin/wine (that would be sudo chmod -x MOUNTPOINT/usr/bin/wine on a liveCD)he would be able to stop the potential spread of the virus allowing him to use sudo again on the infected system.  Then he could use clamscan to move all the "infected" files into a folder, where he could review them and then delete safely.  Then he should delete ~/.wine  That should clean the system.

@OP let me know if you want me to simplify all that for you, dont know how long you've been using linux :)

---

### Post by Rubi1200 on 2010-06-23
> **nerdy_kid said:**
> he cant uninstall wine with out running sudo, running sudo would be plain stupid at this point.  However, by booting of a liveCD, mounting the infected system's root partition and removing executible permissions from /usr/bin/wine (that would be sudo chmod -x MOUNTPOINT/usr/bin/wine on a liveCD)he would be able to stop the potential spread of the virus allowing him to use sudo again on the infected system.  Then he could use clamscan to move all the "infected" files into a folder, where he could review them and then delete safely.  Then he should delete ~/.wine  That should clean the system.


+1 excellent advice!

---

### Post by bodhi.zazen on 2010-06-23
Just run:

```
rm -rf ~/.wine
find ~ -name \*.exe -delete
```

* Those commands will wipe your wine directory, be sure you do not need any data in there. If you do need data, make sure it is not affected before you back it up.

Re-run clamav and you should find fewer or no files.

Look for linux native alternate, try to figure out how you were infected (my guess is via wine) ?

---

### Post by 3Miro on 2010-06-24
> **nerdy_kid said:**
> he cant uninstall wine with out running sudo, running sudo would be plain stupid at this point.  However, by booting of a liveCD, mounting the infected system's root partition and removing executible permissions from /usr/bin/wine (that would be sudo chmod -x MOUNTPOINT/usr/bin/wine on a liveCD)he would be able to stop the potential spread of the virus allowing him to use sudo again on the infected system.  Then he could use clamscan to move all the "infected" files into a folder, where he could review them and then delete safely.  Then he should delete ~/.wine  That should clean the system.


Avoiding sudo might be overly paranoid, but I guess extra precaution is not a bad thing.

I don't see the danger of sudo, unless the computer is still connected to the Internet. I am assuming the computer was unplugged from the network as soon as the virus appeared, right?

I would like to get a hold of this virus to study it a bit. Any guesses on how I can get the original infected file?

---

### Post by nerdy_kid on 2010-06-24
> **3Miro said:**
> Avoiding sudo might be overly paranoid, but I guess extra precaution is not a bad thing.

I don't see the danger of sudo, unless the computer is still connected to the Internet.

viruses like to self replicate whether or not the pc is connected to the internet.... 
Better safe then sorry :D

I was thinking some more though, and he probably could just run sudo chmod -x /usr/bin/wine from the infected system with out too much risk.  That would save him the whole LiveCD thing (cause if he is like me he doesnt have a livecd).

---

