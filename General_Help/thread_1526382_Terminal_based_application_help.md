---
title: "Terminal based application help"
date: 2010-07-08
forum: General Help
---

### Post by tom.swartz07 on 2010-07-08
Hi all,

I have a really simple question.
Im trying to set up my workflow to a terminal-based setup, so that accessing my computer through SSH will provide many of the things I need and use right off the bat.

I have Mutt working great with my GMail account, so that's good.

I do have a question though. Using the application Calcurse (featured on Lifehacker a few days ago, [http://lifehacker.com/5580233/calcurse-managers-tasks-and-appointments-with-pure-text](http://lifehacker.com/5580233/calcurse-managers-tasks-and-appointments-with-pure-text)) I am at a loss to figure out how to interface with Google Calendar. 

Is there a trick that Im missing, or does anyone know of another terminal app that plays better with Google Calendar?





Also, I was looking for a 'Digital Clock', essentially, again,  a terminal/text based large print clock; similar to the one in the lower left corner on the attached pic. Any ideas? I was looking for a telnet server from the Atomic Clock, but no such luck so far.....

---

### Post by tom.swartz07 on 2010-07-08
Bumpity Bump

---

### Post by nothingspecial on 2010-07-08
Don`t know a thing about google calendar, and I don`t know of a large digital clock so I`m not going to be much use

but

Have you tried byobu, which is Ubuntu`s pimped up version of GNU screen.

It comes with a sort of "panel" in which you can have the time displayed along with other info.

If you don`t use screen (byobu) you will find it extremely useful in a terminal only environment.

[ATTACH]162792[/ATTACH]

---

### Post by tom.swartz07 on 2010-07-08
> **nothingspecial said:**
> Don`t know a thing about google calendar, and I don`t know of a large digital clock so I`m not going to be much use

but

Have you tried byobu, which is Ubuntu`s pimped up version of GNU screen.

It comes with a sort of "panel" in which you can have the time displayed along with other info.

If you don`t use screen (byobu) you will find it extremely useful in a terminal only environment.

[ATTACH]162792[/ATTACH]

Ive heard of it, but I'm not particularly thrilled about using another terminal client. I like the ease of Terminator, and its ability to use GTK drawing for multiple terminal sizes. 

I regularly run on several machines, Ubuntu, Lubuntu, and Windows, so I would rather just forward the direct feeds that I need from my host, and pull up a clock display in a small terminator pane. 

Perhaps this may be one that I have to make myself! :sinister laugh:




Anybody know about getting a terminal client version of Google Calendar? Or even to get Calcurse to UPLOAD changes to a google calendar?

---

### Post by Jan Dahl on 2010-07-08
If you have to build it yourself, check out Google's new command line tools. That should make it pretty easy.


As an aside, screen/byobu is not really an *alternative* to your terminal emulator (Terminator or whatnot), but a supplement. Trust me on this, if you like working from a CLI, it is so awesome your ears will bleed. The Byobu project is just making screen useful for the general population. Try it; from your term run byobu. Then hold Ctrl and press A then release and press C (C-a, c). You now have two terminal windows that you can switch between using C-a, space. To change title, press C-a, A. That's just the superbasic idea; there is so much more power in that thing that it often amazes me, even after years of use.

---

### Post by nothingspecial on 2010-07-08
> **Jan Dahl said:**
> 
As an aside, screen/byobu is not really an *alternative* to your terminal emulator (Terminator or whatnot), but a supplement. Trust me on this, if you like working from a CLI, it is so awesome your ears will bleed. The Byobu project is just making screen useful for the general population. Try it; from your term run byobu. Then hold Ctrl and press A then release and press C (C-a, c). You now have two terminal windows that you can switch between using C-a, space. To change title, press C-a, A. That's just the superbasic idea; there is so much more power in that thing that it often amazes me, even after years of use.

I couldn`t agree more, I have used screen in conjunction with terminator before, but now use it with dvtm because screen runs inside terminator while dvtm runs inside screen, you`ll see what I mean if you try it.

Also using byobu, press F2 and you have a new "work space" and again and again and again, they appear in the "panel" like window thingys in a gui panel. Navigate between them using F3 & F4.

Start a process in screen Press Ctrl D, then fly half way round the world, ssh into your box from a different computer, type screen -r and your back, viewing the same process

Screen (byobu) is not a terminal emulator it`s like a DE for the console. Honestly, if you are going to migrate to a console only environment it is one of the most usefull things you can imagine.

(Although you can split the screen with screen, it was dvtm doing that)

---

### Post by tom.swartz07 on 2010-07-08
> **nothingspecial said:**
> I couldn`t agree more, I have used screen in conjunction with terminator before, but now use it with dvtm because screen runs inside terminator while dvtm runs inside screen, you`ll see what I mean if you try it.

Also using byobu, press F2 and you have a new "work space" and again and again and again, they appear in the "panel" like window thingys in a gui panel. Navigate between them using F3 & F4.

Start a process in screen Press Ctrl D, then fly half way round the world, ssh into your box from a different computer, type screen -r and your back, viewing the same process

Screen (byobu) is not a terminal emulator it`s like a DE for the console. Honestly, if you are going to migrate to a console only environment it is one of the most usefull things you can imagine.

(Although you can split the screen with screen, it was dvtm doing that)

Excellent! Thanks for clearing that up!
Im starting to play around with dvtm- I might use it instead of Terminator! less hassle?



Im still trying to figure out how to get a clock similar to the picture I posted. I know byobu has the little clock at the bottom, but I would prefer a larger display, possibly one that could sit in its own dvtm tile?


I already knew about the google command line services, thats what Ive been using for the time being, but I would like to (somehow) get it integrated with an actual client similar to calcurse. I just can't for the life of me figure out how to get the data from *THERE* to here. haha

---

### Post by nothingspecial on 2010-07-08
I`m sorry, I don`t know anything about your actual issues.

Just one word of warning though, as you start to mess around with screen/byobu + dvtm and ssh, it is easy to forget which box you are actually working with - if you have multiple boxes which I assume you do.

I was forever rebooting my server when I actually meant to reboot the client machine (or doing something to one machine when I meant another)

aliases come in handy for this.

---

### Post by tom.swartz07 on 2010-07-08
> I`m sorry, I don`t know anything about your actual issues.
Its okay. I wont hold it against you! :P


> 
Just one word of warning though, as you start to mess around with screen/byobu + dvtm and ssh, it is easy to forget which box you are actually working with - if you have multiple boxes which I assume you do.

I was forever rebooting my server when I actually meant to reboot the client machine (or doing something to one machine when I meant another)

aliases come in handy for this.
Noted. 
I dont usually intend to use this method for Long-Term sessions, simply when Im at University and leave my computer in my dorm, or when Im on the road and need to get some work done.

---

### Post by Jan Dahl on 2010-07-08
I just randomly stumbled upon this screencast that might be handy to learn about screen. Remember that byobu is just screen+user friendliness (I didn't know about those extra buttons, but I'm pretty sure nothingspecial meant Ctrl+A, D)

> **nothingspecial said:**
> Just one word of warning though, as you start to mess around with screen/byobu + dvtm and ssh, it is easy to forget which box you are actually working with - if you have multiple boxes which I assume you do.

I was forever rebooting my server when I actually meant to reboot the client machine (or doing something to one machine when I meant another)

aliases come in handy for this.

That's why my shell always displays hostname ;)

I have this ~/.bashrc everywhere I ssh:
```

# # set prompt: ``username@hostname$ '' 
PS1="`whoami`@`hostname | sed 's/\..*//'`"
case `id -u` in
        0) PS1="[${PS1}]# ";;
        *) PS1="\D{%F %T} \n[${PS1}]$ ";;
esac 
```(Er, and ISOdate+time)

EDIT: Also, I have some clever scripting that someone else found for transplanting hostnames of stuff you ssh into into your screen window title (e.g. if I go 'ssh jan@somebox', the title for that window changes from '0* mybox' to '0* somebox). If you want, I can dig it outand translate it.

---

### Post by nothingspecial on 2010-07-08
> **Jan Dahl said:**
> I'm pretty sure nothingspecial meant Ctrl+A, D)


I did, but it wouldn`t be the first time (today) I`d given someone bad advice due to a typo :p

---

