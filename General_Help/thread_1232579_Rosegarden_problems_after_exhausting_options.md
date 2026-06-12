---
title: "Rosegarden problems after exhausting options"
date: 2009-08-05
forum: General Help
---

### Post by sponsoredwalk on 2009-08-05
Hi i installed Ubuntu 9.04 ona laptop via WUBI and have installed plenty of working programs. Now Rosegarden doesn't work. 

1. I installed Ubuntu Studio as it said it would help with the low latency (i still get that message after installing it). 

2. Jack doesn't work for Rosegarden, if i type qjackctl and then start rosegarden jack doesn't display an error message but i still get the low latency message and there is still no sound.

3. Hydrogen works fine, and this uses similar things to rosegarden.

idk what else to do, can't find any other helpful options through browsing old posts or throughout the internet, i hope it's just down to my lack of Ubuntu beans/ knowledge of linux and not a fatal error. I only installed ubuntu on this laptop for rosegarden and i don't want to go back to vista lol. Please let me know your thoughts, thanx :)

---

### Post by sponsoredwalk on 2009-08-06
Hi so i reinstalled my whole wubi 9.04 linux and i still have no sound in rosegarden. Here are some of the messages i get;

From Rosegarden upon starting i get this;

> Failed to connect to JACK audio server.
Rosegarden could not connect to the JACK audio server. This probably means the JACK server is not running.
If you want to be able to play or record audio files or use plugins, you should exit Rosegarden and start the JACK server before running Rosegarden again.

And there's no sound in Rosegarden, 

If i type "jack" into my terminal i get;

>   :~$ jack
This is jack 3.1.1 (C)2004 Arne Zellentin <zarne@users.sf.net>
 *warning* You have no standard location set, putting files into the current
           directory. Please consider setting base_dir in ~/.jack3rc.
 *info* matching dir found: ./jack-023bfd01
 *error* cdparanoia failed - could not read CD's TOC.          

So i found through browsing random webpages that i can use "qjackctl"


>  :~$ qjackctl
Connection failure: Connection refused
pa_context_connect() failed: Connection refusedSuspending PulseAudio
Connection failure: Connection refused

        (and from jack itself)

ERROR - JACK AUDIO CONNECTION KIT
Could not connect to JACK server as client.
- Overall operation failed.
- Unable to connect to server.
Please check the messages window for more info

       (from the "messages" window in jack)

13:06:51.077 Patchbay deactivated.
13:06:51.804 Statistics reset.
13:06:51.829 Startup script...
13:06:51.830 artsshell -q terminate
13:06:51.839 ALSA connection graph change.
sh: artsshell: not found
13:06:52.650 Startup script terminated with exit status=32512.
13:06:52.651 JACK is starting...
13:06:52.653 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n2
13:06:52.673 JACK was started with PID=7118.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1210808640, from thread -1210808640] (1: Operation not permitted)
cannot create engine
13:06:52.730 JACK was stopped successfully.
13:06:52.731 Post-shutdown script...
13:06:52.732 killall jackd
13:06:52.856 ALSA connection change.
jackd: no process killed
13:06:53.142 Post-shutdown script terminated with exit status=256.
13:06:54.866 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.

        (NOTE: This IS from the messages window :p) 

Now i'm pretty sure i uninstalled pulseaudio using this guide
[http://www.ubuntugeek.com/how-to-remove-pulse-audio-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-remove-pulse-audio-ubuntu-810-intrepid-ibex.html)
[]("http://www.ubuntugeek.com/how-to-remove-pulse-audio-ubuntu-810-intrepid-ibex.html")
and it worked apart from the very end where is says 
> Finally Your asoundrc’s under your Home Directory are still configured for Pulse.



Go to your home directory using the following command

cd ~

cp .asound* yourfilename

    rm .asound*

though i assume that is trivial.



Also, i still get this message. 
>    System timer resolution is too low
Rosegarden was unable to find a high-resolution timing source for MIDI performance.
You may be able to solve this problem by loading the RTC timer kernel module. To do this, try running sudo modprobe snd-rtctimer in a terminal window and then restarting Rosegarden.
Alternatively, check whether your Linux distributor provides a multimedia-optimized kernel. See [http://rosegarden.wiki.sourceforge.net/Low+latency+kernels](http://rosegarden.wiki.sourceforge.net/Low+latency+kernels) for notes about this.                                           

I have ubuntu studio installed and i thought that would alleviate the problem, which it didn't.

Quite a difficult problem here, sincerely appreciate any help. 

Amabo Te. (:

---

### Post by sponsoredwalk on 2009-08-06
Now i found something i totally don't understand,

>   cat jackreaper
/usr/bin/jackd  -t10000 -dalsa -dhw:0 -r44100 -p4096 -n2 -D -Chw:0 -S -i2 -o2 -I170 -O170  

I found this little code @ [http://www.linuxquestions.org/questions/linux-software-2/qjackctl-could-not-connect-to-jack-server-as-client-567108/](http://www.linuxquestions.org/questions/linux-software-2/qjackctl-could-not-connect-to-jack-server-as-client-567108/)

and i followed the instruction to change -p4096 to -p1024. and i don't get the jack message coming up in rosegarden anymore, but i STILL hear no sounds... it's the closest i've gotten but A) it's a total hackjob and not a proper solution and B) i have no sound from Rosegarden. There has to be a way to fix this

---

### Post by sponsoredwalk on 2009-08-07
Ok, after about 15 hours of googling and worrying about the fact that i should of been studying i have come pretty close but i stil need help.

THE GOOD: I got sound out of Rosegarden!!!
This brave soul who went to the trouble of writing up a guide should be regarded in high esteem by all,

[http://www.linuxquestions.org/questions/linuxquestions.org-member-success-stories-23/setting-up-rosegarden-for-midi-music-in-linux-ubuntu-8.04-697198/](http://www.linuxquestions.org/questions/linuxquestions.org-member-success-stories-23/setting-up-rosegarden-for-midi-music-in-linux-ubuntu-8.04-697198/)

I wish more guides were written this way, well only for the really weird or hard stuff you want to install. I never usually have any issues because the standard ubuntu walkthru's are really easy to follow.

THE BAD: This is using ALSA!!!
Now it should be using JACK and i would have no problem bending the rules and using alsa but you'll see why i need jack in the next section (the ugly). 

So i worked through the jibberish (to me) that is a user-manual and found that to use jack with rosegarden i was supposed to type the following into terminal, i never seen that i was supposed to do it in a specific order it was pure chance that it happened and i seriously think that the people who are in charge of JACK have a lot to account for, i'm not the only one who has problems with it and i have found countless posts with people having issues with it.

First this,
>  jackd -d alsa -d hw -r 44100 -p 2048 -n 2 
Then in a new terminal tab,
> qjackctl

That way i got no error messages saying jack wasn't working. HOWEVER, there was still NO SOUND!!!


THE UGLY: I could care less about all of the above if i could find a way to bend the rules further and record the song i made on Rosegarden to a file, any file... I have a sweet setup, it's mixed with Hydrogen and i have for the first time gotten this program to work (over a year on a slow computer so never had this horse power b4:()

Is there a way to record the music that plays out of my speakers to a file? Audacity records no sound or wont even allow me to record. Sound Recorder doesn't allow me to record any sound either, only emptiness. I have no option in either of the programs to record from the mixer or anything like that.

(btw when i export the midi file it only plays a snare drum hitting repeatedly, i didn't make it AND ROSEGARDEN DOES NOT ALLOW RECORDING TO A TRACK WITHIN ROSEGARDEN WHEN U USE ALSA!)

Please help!!!

Amabo Te :(:(:(:confused::P:P:P

---

### Post by ellgor on 2009-08-07
Hi,

Try "Ardour" much easier and simpler and works out of the box.

Regards, Ellgor.

---

### Post by sponsoredwalk on 2009-08-07
Ardour doesn't have the power of Rosegarden, nor the ability to make piano, violin, and mix it with hydrogen drums. It's a program worth fighting for, all my above worries still stand and really hope someone can help me fix them:KS:KS:KS

---

### Post by sponsoredwalk on 2009-08-07
Oh sorry, and I forgot to mention, Ardour doesn't work when i have the other programs open, so i have no program (that i know of)with the capability to record the overall mix the music i made to a .wav/.mp3 file etc... Finding a sufficient fix to this problem is enough for me, i know it's a half-fix but i would assume future versions of ubuntu would have these issues ironed out... :popcorn:

---

### Post by sponsoredwalk on 2009-08-07
GOT IT!!!! I GOT IT!!! WOO WOO WOO I <3 UBUNTU. WIll post a full walkthrough a FULL walkthrough for all who've felt the burn of this piece of machinery for total noobs after the weekend, gotta go but shall be very happy :)

---

### Post by ellgor on 2009-08-08
Hi,

The Ardour I use has all the functions you describe, just not already built in, if you go to the Ardour site they have plugins for every conceiveable instrument, synthesiser, the works.

Regards, Ellgor.

---

