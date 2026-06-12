---
title: "Remote computer control through SMS - Ideas?"
date: 2010-04-27
forum: General Help
---

### Post by Draco Advigilat on 2010-04-27
First off, let me say I'm sorry if there was a more appropriate part of the forum to post this, but it's an unusual question and I couldn't think of how to categorize it.

Additionally, this is something that I want to do just for the fun of it, so if you think I'm silly for trying, you might as well stop reading here. I don't want to waste anyone's time.

As for what I am trying to do: I am looking for a way to run scripts and/or launch programs from a cell phone using SMS. I've found a few options close to this, but nothing that really fits what I'm trying to do. It seems I can either get speed or ease of use, but not both. To explain:

If I understand correctly, Evolution has this functionality through email, but email isn't instant. I'm trying, as best as I can, to use my phone almost like a remote; sending email from my phone would create a considerable wait time.

Using Pidgin's Buddy Pounce feature with AIM lets me use SMS to get a quick response, but I'm running into the problem that I can't make its action depend on what the message says. I want to be able to text, say, "Shutdown", and have my computer run a shutdown command, but Pidgin's Buddy Pounce feature doesn't seem to support checking for specific messages. I've been unable to find a plugin that changes this; if there was, it'd probably be my best bet.

Bluetooth is out; my computer's bluetooth adapter died a long time ago. Additionally, some of the things I'd like to do would be when I'm not near the computer, so even if it was functional, it would be limiting.

Anything that requires any apps for android, iPhone, or w/e are out too. I have an LG Dare, and while it's a nice phone, you can basically forget custom apps.

So, to recap, I'm trying to find some way of sending an SMS or email from my phone, have it be received as quickly as possible, and have the computer run a console command based on the content of the SMS/email. Any ideas?

In case it's relevant, I'm running Ubuntu 10.04.

---

### Post by llamabr on 2010-04-27
Sounds pretty dangerous.

In any case, are you running a mail server right on your box?  You could probably rig up a procmail recipe to execute those commands.  though of course, doing so would allow anyone to do that.  And since you want things like shutdown, it would allow anyone to run root commands, right over the internet.

---

### Post by arjunbajaj on 2010-04-27
Hey Dude,

What an Idea.......

I dont have any suggestions but if you can get an appropriate app for android then you can do one thing......... 

if lg dare has a good processor then goto xda developers and try installing windows mobile 6.5......if that happens then search there for android for windows mobile 6.5..... it will be a file you will have to execute and that if works will start android...........


then after that search for an appropriate app on some forum for android remote control.......then try using that.......could be its a bluetooth based app......so its better to buy a small bluetooth dongle.......they are damn cheap now days..........but first try running windows mobile 6.5 and then try running android..........


backup ur data and keep a rom of your current lg dare os.........because could be that the installation of windows mobile works but ur android doesn't boot up......then to roll back u will have to put ur old rom............




and i have an asus p320. i had windows mobile 6.1 installed on it.....i installed windows mobile 6.5 but still my mobile isn't able to boot android up.......




and ur idea is great......if you made it to work with sms or email it will be great..........

:):)

---

### Post by Draco Advigilat on 2010-04-28
To respond first to the android OS hack idea, I've already looked all over to see if there's anything tricky I can do with the LG Dare and found next to nothing. Unless I'm missing something, that's simply not happening. Thanks for the idea, but no luck there.

On the thought of it being dangerous, the implementation that I'm looking for shouldn't be to bad. I should have clarified earlier that when I gave the example that "shutdown" would shut down the computer, I didn't mean that I would be texting the command I wanted to use. Rather, I was hoping to find something that would check the contents of the email run a command based on words/phrases I define. A better example would be texting "Play music" to open and start Rhythmbox. (Outlook Express had this sort of functionality, and I was hoping I could  find a comparable option for a Linux based email client.) Done that way, it might be possible for people to do things to my computer, but nothing more than I had set up, in theory. I'm well aware that the setup isn't terribly secure either way though.

I should also mention that I've been nearly successful, if anyone was interested in a solution themselves. Thunderbird, when "Check every x minutes" is turned off and using the IMAP protocol, will pick up new email as soon as you receive it. (Evolution, with the same settings, will wait until you click to manually receive new email, which it was not a viable solution) On my phone, I can text to an email address just as easily as I can send text through SMS. All together, there's only a slight delay; not bad overall.

Additionally, it supports filters and actions, which let you check for what the message contains and perform different functions accordingly. The filters are exactly what I need, but the only thing that's lacking at this point is the ability to run a script or terminal command. I am looking for a plugin for this, but it's late, so I will continue the search tomorrow.

As a proof of concept though, I did find this: [https://addons.mozilla.org/en-US/thunderbird/addon/2610](https://addons.mozilla.org/en-US/thunderbird/addon/2610). It works as a proof-of-concept, if you want to call it that. I tried setting it up so that I could text commands to control Rhythmbox and was able to pause, play, skip tracks, and whatnot fine. My only frustration with it is the aforementioned security problem: it has to be used to run command lines directly, rather than using a user-defined list of keywords. Because of that, I'd disabled it, and don't plan on leaving it running for any length of time.

So, tl;rd? I have it almost working. Just need to find a better plugin, or consider writing one my own.

Thank you for the ideas and for pointing out the potential security issue.

---

### Post by Grenage on 2010-04-28
Take a look at the gsm-utils suite, I use gsmsendsms to pipe messages out of Nagios to mobile phones; it includes utils for taking SMS messages off sim cards.

There is no reason you couldn't parse received messages to perform tasks on a computer.

---

