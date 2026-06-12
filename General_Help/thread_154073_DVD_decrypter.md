---
title: "DVD decrypter"
date: 2006-04-02
forum: General Help
---

### Post by GreveFelix on 2006-04-02
Hello everyone,
just another little question,.... if you dont mind:

Which programm should I use to transfere a hole DVD to my Harddisc? It should be able to crack CSS and import the hole DVD stuff (incl menu)...

Thank you .......

---

### Post by stoeptegel on 2006-04-02
There's xdvdshrink and dvd::rip. I don't know wheither they do menu or not though.

---

### Post by xXx 0wn3d xXx on 2006-04-02
[QUOTE=GreveFelix]Hello everyone,
just another little question,.... if you dont mind:

Which programm should I use to transfere a hole DVD to my Harddisc? It should be able to crack CSS and import the hole DVD stuff (incl menu)...

Thank you .......[/QUOTE]
You could try dvd::rip. I have used it and it works great.

---

### Post by GreveFelix on 2006-04-02
Thanks for your suggestions! I tried to install dvd::rip via synaptic-install programm. But now I dont find the programm dvd::rip in my Programspannel.... how do you use dvd::rip???

---

### Post by xXx 0wn3d xXx on 2006-04-02
[QUOTE=GreveFelix]Thanks for your suggestions! I tried to install dvd::rip via synaptic-install programm. But now I dont find the programm dvd::rip in my Programspannel.... how do you use dvd::rip???[/QUOTE]
I should be under Applications > Sound & Video > dvd::rip. I used automatix to install it so you can try that.

---

### Post by GreveFelix on 2006-04-02
Ok thanks I found it under:
file:///usr/share/ubuntu-docs/generic/faqguide/en_AU/sample/dvdrip.desktop_dvdrip
and then started the programm, it really looks quite userfriendly.... But the programm said it has some problems with the transcode/libdvddread is it a codec? Maybe it is not installed ... 

and It just loaded the trailers on my harddisc and not the main movie ..

In the beginning it tould me: "Failed to copy the IFO files. vobsub cration wont work properly. (did you specify the mount point of yur DVD drive in the preferences?)"

But I thing the mount point is OK , because otherwise it whoud not be able to download the trailers (or not?) 


Thanks again for quick replies ... this is such a great thing this hole forum and Ubuntu too , I am really exited about that!

---

### Post by xXx 0wn3d xXx on 2006-04-02
ok, maybe we should try automatix ? Do sudo apt-get remove dvd::rip to remove it and then install automatix.

In terminal, copy and paste the following, one line at a time.

wget [http://beerorkid.com/automatix/automatix_5.7-3_i386.deb](http://beerorkid.com/automatix/automatix_5.7-3_i386.deb)
sudo dpkg -i automatix_5.7-3_i386.deb

Pick the things that you want to install and also anything that you find interesting.

---

### Post by Iandefor on 2006-04-02
[quote=GreveFelix]Ok thanks I found it under:
file:///usr/share/ubuntu-docs/generic/faqguide/en_AU/sample/dvdrip.desktop_dvdrip
and then started the programm, it really looks quite userfriendly.... But the programm said it has some problems with the transcode/libdvddread is it a codec? Maybe it is not installed ... [/quote] Transcode is a program that can copy DVD movies and encode them, etc. DVD::RIP is little more than a frontend to it.
libdvdread is a library that enables programs to crack the CSS encryption used by DVD's. 

You might not have them installed, but if you didn't, you wouldn't be able to rip those trailers. Try running the command 'transcode' on it's own in a terminal and see what it returns (Post it here!).

@Masterchief1234:

I would recommend a purge of the program, since just removing it doesn't get rid of the configuration files. It might cause conflicts later in the automatix install process to have old configuration files lying around.

---

### Post by GreveFelix on 2006-04-02
Ok,
I deintalled DVD::Rip via synaptic and then ,,,

felix@Vincent:~$ wget [http://beerorkid.com/automatix/automatix_5.7-3_i386.deb](http://beerorkid.com/automatix/automatix_5.7-3_i386.deb)
--19:48:40--  [http://beerorkid.com/automatix/automatix_5.7-3_i386.deb](http://beerorkid.com/automatix/automatix_5.7-3_i386.deb)
           => `automatix_5.7-3_i386.deb'
Auflösen des Hostnamen »beerorkid.com«.... 208.97.133.175
Connecting to beerorkid.com|208.97.133.175|:80... verbunden.
HTTP Anforderung gesendet, warte auf Antwort... 200 OK
Länge: 33,730 (33K) [text/plain]

100%[====================================>] 33,730        44.05K/s

19:48:42 (43.94 KB/s) - `automatix_5.7-3_i386.deb' saved [33730/33730]

felix@Vincent:~$ sudo dpkg -i automatix_5.7-3_i386.deb
Wähle vormals abgewähltes Paket automatix.
(Lese Datenbank ... 77638 Dateien und Verzeichnisse sind derzeit installiert.)
Entpacke automatix (aus automatix_5.7-3_i386.deb) ...
Richte automatix ein (5.7-3) ...

Its german and it says it installed automatics, but now how do I use it ? :-k 

Sorry, I know maybe this is a very dump question ...

---

### Post by Iandefor on 2006-04-02
It's under Applications-->System Tools

And I don't think it's a dumb question. The recommendation to install Automatix negelcted to point out where it could be located :).

---

### Post by GreveFelix on 2006-04-02
Ok I did that and istalled dvd rip via automatics but .. still this error occured:

"Failed to copy the IFO files. vobsub cration wont work properly. (did you specify the mount point of yur DVD drive in the preferences?)"


I whould be greatful for any suggestions ...

---

### Post by GreveFelix on 2006-04-02
To make it clear: It wrote the Trailes on my Harddisc but not the main movie.
It gave me this error message:

Failed to copy the IFO files. vobsub cration wont work properly. (did you specify the mount point of your DVD drive in the preferences?) could not mount the mount point /dev/dvd (mount : block device/dev /hdc is write-protected , mounting read-only 
mount:/dev /hdc already mounted or /media/cdrom 1 busy 
mount: according to mtab, /dev /hdc is already mounted on /media/cdrom1

Do I have to change something ?

---

### Post by MetalMusicAddict on 2006-04-02
On a side question. Why doesnt DVD::Rip use GTK2? Its always looked really bad and very large on-screen.

---

### Post by GreveFelix on 2006-04-03
Oh,
I am sorry I dont know what GTK2 is and I dont know why dvd::rip do not use it. 
(You see I dont know much #-o  (at least not much about Ubuntu...) but I am here to change that! 

Could somebody explain what is a dvd mount  point? Should I write there the same as I wrote in the first line under Preferences? I gues not because it tould me there is a write protection and this whould not fit with a dvd, right ?? Maybe somebody who is using dvd::rip could tell me what he wrote in the preference menue and .. why?

This whould be very nice of you..... :KS

---

### Post by GreveFelix on 2006-04-04
Ok just in case somebody is still interested:
I changed the DVD mount-Point to: "/media/cdrom1" and after that I was able to get the hole movie on the harddisc ...

;)

---

### Post by tsb on 2006-04-04
I think using DVDFab Platinum with Wine is the best.  Just follow the DVD Decryper guide, but use the DVDFab setup exe instead.

---

