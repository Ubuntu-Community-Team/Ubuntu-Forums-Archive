---
title: "Mythbuntu has grinded to a halt"
date: 2010-02-18
forum: General Help
---

### Post by the goat boy on 2010-02-18
Hello again

I am finally on the verge of ditching Mythbuntu after a long and unhappy relationship

It has taken me an age to get it all up and running to a good point, and now one update has ruined the box.

I am running Mythbuntu 9.10.

Last night I ran the usual system update, and since then, the box is f*cked. It won't run for more than 5 seconds now without hanging. even if i run anything from the command line, it just keeps pausing.

it is not possible to watch any videos, or even use the box anymore.

I am totally fed up with sh*t like this happening all the time

i am 10 minutes away from ditching it all, and starting again on Windoze.

I am not a complete linux newbie, but I have never experienced any problems with any of my other systems.

can someone please offer me any help as to what I can to do to fix this, otherwise the box I have under my TV is one expensive brick.

pleas please help :-(

---

### Post by kubug on 2010-02-18
I hear your frustration. It can can be quite aggravating when your hard work doesn't pay.

But do you have some more info for us? Like what hardware you are running, have you checked your log files what they say before it hangs? Any changes you made?

---

### Post by the goat boy on 2010-02-19
OK. Here goes

I have a shuttle PC, with an AMD processor. Can't remember the details. It has a Hauppage (please excuse spelling) S2 Satellite card, 500 Gb hard drive (over 13- Gb spare)

I haven't made any changes to it, apart from running the update manager as I was "43 days out of date"

As for logs, I can see in Dmesg the line:

Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.

which sounds a bit ominous.... not sure how long ago that was in place, but it should not be low on RAM. I am sure I have 2 gig in there.

Its a total nightmare at the moment. I am on the command line, and when i type its a good 15 seconds behind. and I am not the fastest keyboard wizard about.

Any other logs worth a gander at???

oh, also in /var/log/messages it seems that its waiting for firmware to load

why would this have changed?

---

### Post by kubug on 2010-02-19
I am certain that there would have been a kernel update in there. Do you have any drivers in use that needed to be compiled? You may need to re-compile those again for your TV tuner card.

Do you get a graphical display or only a command line?

---

### Post by kubug on 2010-02-19
For your RAM, a quick look at "top" would show you. Have you used that before?

Just enter "top" on the terminal line and it should display the total RAM, used RAM, as well as CPU usage. Check to see if there is something using the CPU extensively, which would explain the slow typing process.

---

