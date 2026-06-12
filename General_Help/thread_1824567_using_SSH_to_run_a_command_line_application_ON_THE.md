---
title: "using SSH to run a command line application ON THE SERVER"
date: 2011-08-13
forum: General Help
---

### Post by asomad on 2011-08-13
Ok Ill try to keep this simple. Im a linux noob, but faaaar from a computer noob.

Ive been playing with Ubuntu 10.04 in a CLI only environment, mainly just to tinker and learn. I do this via my windows7/Ubuntu-gnome laptop, using ssh. On windows i use PuTTy, or if booted into Ubuntu/Gnome, I open a terminal and ssh command to connect to my "server" and sit comfortably on my couch, with my laptop and access my server's CLI and play.

Some applications act differently when run remotely, versus when I run the application at the server itself.. I can postulate several theories why (perhaps the differences in the shells that are launched through a SSH connection versus locally at the actual machine?).

Specifically. In front of my ubuntu CLI machine, I like to use an app called mp3blaster. It works lovely. However, via a SSH connection from my laptop, I can run mp3blaster, but when I try to play a track I get a "failed to open sound device" error. This happens via Putty in windows and also through a terminal in ubuntu/gnome on my laptop, SSH'ed to the "server". I'm sure the issue obviously is because i'm trying to operate an audio application through SSH. due to my inexperience with linux, I lack even the proper terminology to search for a way around this problem.

####I want to, via command line, through a SSH connection from my laptop, run mp3blaster to play audio tracks on my server, with the sound being piped out of the SERVER'S audio port (it's the nicest sound system in my house :-)).#####

I have considered maybe, From my laptop, in Ubuntu and gnome open a terminal, and use an rsh command to run the application @the "server". problem, Sure the application might be running on my server at that point, but I wont be able to get to it anyways because it wouldn't be running in either bash shell, on my laptop or on the server....

Thoughts? direction? ideas? Using a SSH command line terminal is important to me for this specific project. 
Even with graphical solutions, and even through remote desktop, I think it would be STICKY getting the sound to play "on the server" vs "on the client"?

######I'm hoping there's a simple switch or command I can put in front of the application to make it launch "as if it was launched at the machines own bash" like "$ -<magic problem solver> mp3blaster"#####





note: I KNOW there is a million ways I could pull this off. I want to do it THIS way. ;-)    It would be another plus of ubuntu in my book....

---

### Post by Toz on 2011-08-14
That's odd. I can't get mp3blaster to work at all on the host. However, if I start it with padsp, it works. Both on the host and through ssh. Try:
```
padsp mp3blaster
```

---

### Post by asomad on 2011-08-14
nope, same thing. Ive got my SSH opened up (i.e. insecure) and my account i log in with has root permissions. Have no problem opening mp3blaster through SSH, it just wont play the file.... Just wish I could shout at it "pretend i'm running you from over there!!!"

---

### Post by asomad on 2011-08-14
Or, perhaps change something with bash itself, so it runs **exactly** the same way via SSH as it does through the servers monitor and keyboard? Or something along that line of thought. To the right person, this will be a simple teaching/solution. Maybe something in the ssh config itself? I couldnt find anything in the documentation. but my terminology is lacking....

---

### Post by Sazhen86 on 2011-08-14
Hi

It's a long shot, but it you're using ALSA for the playback, you need to set the environment variable SDL_AUDIODRIVER.  Maybe this is being set when you log into the server locally, but not when you use SSH.

Cheers

---

### Post by asomad on 2011-08-14
maybe an SSH connection does not have access to the sound by default?

---

### Post by asomad on 2011-08-14
Im going to look into that. I'm thinking this may indeed be related to environmental variables, or something of the like, being different via ssh........ I feel like i'm on the right path at least now, thank you. When I wake up ill compare the "env" results both locally, and via my ssh login, and I'll go from there.

---

### Post by asomad on 2011-08-14
ok so the environmental differences in the shells local at host vs remote through ssh. The TERM=linux on the sever, and on the ssh client TERM=xterm. both shells show /bin/bash, so why does the SSH teminal act differently when running apps versus running the app AT the host... the only other environmental differences are the SSH bash gives extra details about the SSH connection. 

Still not well versed enough to figure out a way to make command line aps run EXACTLY as if I'm running them AT the host.

---

### Post by Sazhen86 on 2011-08-15
Have you tried running mp3blaster with the --debug switch enabled?  This might give you a clue as to what is going on.  Also are you using the default sound device which is /dev/dsp?  If so, perhaps you can run lsof | grep /dev/dsp to see what is using it.  

Finally, you aren't still running mp3blaster on the server at the time you run it via SSH are you?

---

### Post by asomad on 2011-08-23
After much tinkering... The issue is NOT related to the software I'm using....

I am able to get sound from the server, via an SSH connection. BUT, I must be logged into the server locally as well..... 

So my options are.
-Figure out how to get sound to load, before I log into the server locally, (so I don't have to go log in when i want to use it, this defeats the purpose of using SSH)

-or, make the server Log-in to my account automatically when it's started up, so sound will work when I open an SSH terminal...

If anyone who knows how I can make sound load before a local (or any) login occurs, please let me know. As a noob, I'd be grateful.

Thanks

---

### Post by Sazhen86 on 2011-08-24
It sounds like the OSS devices aren't being created before you login.  What are the differences between lsmod from the console or via SSH?  You could try loading the snd_pcm_oss module from the SSH session to see if it creates the sound device.

---

### Post by asomad on 2011-08-24
Ok, so lsmod shows that all modules are loaded identically, if logged in SSH with NO local logon, through SSH with a local login, and AT the server terminal. All 3 scenarios, show exactly the same lsmod output, not one little difference whatsoever....

So, perhaps SSH doesn't have access to the sound without the local login active (unlikely I think) OR, this issue has to do with upstart or something else not allowing the sound to be accessed until a local login has occured.... 

I don't know if it's worth the troubles at this point. Im going to look into whatever controls the pre-login part of the OS, to either force the server to auto-login at startup, or tweak something to allow sound to work before the local login.

---

### Post by decoherence on 2011-08-24
1. are kernel modules really loaded when a user logs in? i didn't think they were but i guess they could be. does ubuntu do it like that?

2. what environment variables have to do with sound devices? I don't have any SDL_AUDIODRIVER variable in my environment and my sound works fine. Mind you I'm on Fedora. Does mp3blaster use SDL for playback?

when you run mp3blaster locally on the server and it works, are you running it as the same user you are using to log in with ssh? you should be.

are you certain mp3blaster isn't already running when you connect via ssh? it shouldn't be.

is something else using your sound card? i think this is unlikely since you say it's a server and you probably don't have much other than mp3blaster which CAN use your soundcard.

for troubleshooting, i'd try installing another mp3 player and trying that to see if the problem is particular to mp3blaster. personally, i like mpg123 for my command line music.

---

### Post by decoherence on 2011-08-24
Just trying to reproduce your problem. 

When I run mp3blaster either locally or remotely I'm told it can't open the sound device. The fix for this, for me anyway, is to run 'padsp mp3blaster' which makes it work either locally or remotely, with sound coming out of the "server's" speakers.

I use mpg123, either locally or remotely, it works as expected: the audio comes out of the "server's" speakers.

Based on this I would suspect this is an issue with mp3blaster. At the very least, it probably doesn't have anything to do with missing modules or environment variables (though it could be mp3blaster needs some environment variable that mpg123 doesn't.)

Your initial assumption that being logged in via ssh should be nearly the same as running locally is correct. You do not have to worry about redirecting things and if you log in as your regular user, all of your environment variables are the same.

Thus it is very strange that it works locally and not remotely. Please let us know if running mpg123 or padsp mp3blaster works for you.

[add] just re-read the first part of this thread and saw you already tried padsp mp3blaster. still curious to know if mpg123 works, tho

---

### Post by asomad on 2011-08-24
> **decoherence said:**
> 1. are kernel modules really loaded when a user logs in? i didn't think they were but i guess they could be. does ubuntu do it like that?

2. what environment variables have to do with sound devices? I don't have any SDL_AUDIODRIVER variable in my environment and my sound works fine. Mind you I'm on Fedora. Does mp3blaster use SDL for playback?

when you run mp3blaster locally on the server and it works, are you running it as the same user you are using to log in with ssh? you should be.

are you certain mp3blaster isn't already running when you connect via ssh? it shouldn't be.

is something else using your sound card? i think this is unlikely since you say it's a server and you probably don't have much other than mp3blaster which CAN use your soundcard.

for troubleshooting, i'd try installing another mp3 player and trying that to see if the problem is particular to mp3blaster. personally, i like mpg123 for my command line music.

you keep saying mp3blaster, mp3blaster, mp3blaster.......... 
This issue has nothing to do with what I use for the playback! I can't stress that enough! Regardless WHATEVER program is used, the sound device can not be accessed by the program, UNLESS the server has a local login, at it's terminal. Then the SSH terminal has access to sound. Regardless which software you use.

I am way past troubleshooting....... Already verified, ALL of the many programs I tried, CAN play audio through the server. BUT ONLY IF THE SERVER HAS A LOCAL LOGIN ACTIVE AT THE SERVER. I wonder if it helps that the local login is the same user as the ssh login, maybe thats why my ssh connection is allowed access to audio one I log in locally, cause the audio is then tied to my username? Im just thinking here...

At this point in my endeavor, I need to figure out why that is the case, so I can get the sound to work (from SSH connection) without going to the server to login as well. ...

or simpler, I'm just gonna end up making the server auto login upon start.....

(I really think this issue is because this particular Ubuntu install has gnome but is used as a server/CLI), gnomes X is disabled by default, with an edit to gdm.config to start on runlevel [3], so instead of loading the gui it goes to a text login screen. Perhaps if GDM is removed entirely, then it will be a true no gui server, and hence maybe the "no audio via SSH without local login" issue will disappear)


this is the umpteenth time someone has chimed in with trying to test mp3 blaster. forget about testing the audio programs itself, this issue has to do with the nature in which my pc starts up and handles it's log in.... everything I can try, WORKS when server has a local login, and CANT work when it doesnt.

---

### Post by asomad on 2011-08-25
I can even go a step further here, and let it be known, that when the local session is logged out, the sound is cut off to the ssh terminal.

So sound only works on the server if there is a local bash login ACTIVE.

maybe that's just how it's supposed to be..... blah

So, I guess Ill have to make the server log in automatically? If thats even possible with the the command line login..? I hate being a noob to linux, but I have learned ALOT and quick too.

---

### Post by decoherence on 2011-08-25
> **asomad said:**
> I can even go a step further here, and let it be known, that when the local session is logged out, the sound is cut off to the ssh terminal.

So sound only works on the server if there is a local bash login ACTIVE.

maybe that's just how it's supposed to be..... blah

So, I guess Ill have to make the server log in automatically? If thats even possible with the the command line login..? I hate being a noob to linux, but I have learned ALOT and quick too.

Oh, I forgot to test that part of it. I can try it a bit later today.

In any case, that's not how it's supposed to be but it's possible that's how it is and i would consider that a problem. i've triggered all sorts of multimedia type stuff remotely over the years, from playing music to capturing video. mind you I wasn't doing this with ubuntu but in my gut i want to say it shouldn't make a difference. 

in any case, i'm curious now so i'll definitely check it out at some point today.

---

### Post by aravind kamath on 2011-08-25
[B][SIZE=4]touch: missing file operand
Try `touch --help' for more information.[/SIZE][/B]
[SIZE=4][I]
cant create a new empty file...please help[/I][/SIZE]:confused:

---

### Post by asomad on 2011-08-25
@decoherence. THANKS in advance.... 

I hope this probelm is solveable, but due to it's nature I worry that no one will ever be able to pinpoint the issue..... I mean it could be my SSHD (maybe it needs specific permisson or config to have its OWN access to sound), (It could be upstart? Maybe it keeps sound disabled until there is a local login)(maybe its GDM because it's installed, but disabled with an edit to paramaters keeping it from loading unless you use startx command) I mean who really knows. Ive even tried daemonizing pulseaudio, and even that way, no programs can access the server's sound without the local bash session logged in...

Worst case scenario, Ill just look into making the server login to a session automatically upon startup. That is perhaps the simplest solution I can find.

This has been being a terrific learning experience for me. I've been toying with linux for only about 6 weeks now, and I've gotten pretty far. LOL


(edit: my method of disabling gdm and x, is not the cause of this little problem. I had first learned that disabling GDM was better done using the edit to gdm.conf.. the other option is use the grub2 loader edit LINUX_DEFAULT="text" this option was once labeled as not supported (now it seems it is the opposite). I had the runlevel edits in the gdm.conf file. To verify this was not the cause of "no sound without local login", I restored the gdm.conf file to its original state. and now am using the grub edit to disable gdm and X, and boot in text mode. the results are the same. no ssh connection can access sound unless the server has a local session logged in.)

---

### Post by asomad on 2011-08-25
> **decoherence said:**
>  I wasn't doing this with ubuntu but in my gut i want to say it shouldn't make a difference. 
.
no it shouldnt make a difference. but it just might. Specifically because of programs like "upstart" now being used. 

(Im a noob, but apparently upstart handles some of the boot up stuff, and apparently it does it in a very different fashion than linux users are used to.)

---

### Post by asomad on 2011-08-25
SOLVED. 

By default (I think), the only user in group "audio" is "pulse".

adding your username to the group: audio, allows your user access to the servers sound via a SSH connection, without a local login...

thanks to everyone for the help and direction.

---

