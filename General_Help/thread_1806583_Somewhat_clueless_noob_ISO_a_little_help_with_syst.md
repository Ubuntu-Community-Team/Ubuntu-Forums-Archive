---
title: "Somewhat clueless noob ISO a little help with system hardening."
date: 2011-07-17
forum: General Help
---

### Post by stevennlv on 2011-07-17
Hi everybody,

A little about me: I'm an old fart. (Down right  ancient in the computer verse, i.e. over 12.) I was crawling the  ARAPANET from a trash 80 with a spider back in 82 from the home terminal  of a scientist type guy that lived next door. I remember when ABASIC  was hot stuff. And when dirt was new I could do a very little very basic  coding. But, that was probably before a lot of you were even born. Then  they came out with a bazillion new languages and I gave up trying to  keep up. Back then it seemed like a new language cropped every three  days. So I gave up on 'puters for about 10 years.

In the early  90's when the net started to become a thing I went and got a pile of  parts and figured out how to turn it in to a '95 box. (No dell back then  and "out of the box" boxes were insanely priced. They cost like $400  man!)

Fast forward almost 20 years: I consider myself to be an  advanced windoze end user. I couldn't code my way out of a wet paper bag  with a bulldozer and a flamethrower. But, if it's point and click I can  make it do back flips.

I can "harden" a windoze install in my  sleep. (And yes, I realize that's a joke. Please don't poke too hard,  it's still a tender subject.)

So I got this shiny new box from dell with lots of bells and whistles, good stuff Maynard.

Of course I wiped the drive, put a fresh install on it and "hardened" it. (HAHA)

And I've spent the last two months getting re-infected with horrible, gross, ugly nasties every two week like clock work.

So, start over from scratch for like the 5th or 6th time.

This  time I have used VM player to build an Ubuntu net appliance. I'm  running 7 on the box. There's just too much I need to do that is too  much of a pain in the butt in *nix. (Games, printing, etc.) I don't want  to spend lots of time tinkering. I want to point, click and be done.

So  I've set it up to where there is as little "communication" as possible  between the "two" machines. (No unity or shared folders, reset to state  and all that fun stuff.)

I'm using the Ubuntu VM as my general  web surfer. My basic ideas is if I absolutely have to have a file for  the windoze side of the machine I can DL it here then mail it to myself  at yahoo. Then when I retrieve it, it'll be run through their virus  filter before I drop in in my 'doze box. (Hopefully this scheme and tons  of other new stuff I've done this time will keep this friggin thing  clean long enough for me to fully configure it to my specs and shoot a  *^%^&%$$^&%%$ back up!)

I want my UVM to be as hardened a  possible. I don't want some script kiddie poking lots of holes in it. I  just want it to work so that I don't have to keep rebuilding it. Plus, I  figure the harder it is the less likely something is to crossover from  the VM to the "real" box.

I've done some basic things already,  like made sure remote desktop was not enabled. I've installed  firestarter and configured it. I'm wainting on Avast! to send me one of  their free keys so I can get that up and running. (And, yes I want AV.  The whole point of this exercise is to basically create a super-duper  sandbox for surfing on my 'doze box. And I'm thinking I'll be sending  stuff to that side of the box on a fairly regular basis.) I have FF all  tweaked out with spiffy stuff like NoScripts and AdBlock, etc. I've  installed all of the security and recommended updates. But, I know  there's more to do.  

And this is where I need you guys help.

I've  been reading around the forums on how to harden my install. I've found  some "how to guides for noobs" stuff. I guess I'm too stoooopid to  comprende. 

The guides say stuff like: "Grab your favorite text  editor, open XYZ file and input code ABC". Um, where is da file at  George? And is it like notepad? Just type, save and done? Or is there  more to it? Do I have to reboot the VM? Do I put code ABC any place in  particular; end, beginning, doesn't matter? 

The guides also say stuff like: "Open terminal and input this." OK, gotcha, not that dif from cmd prompt.
But the input is formatted like this:
xxx / xxx / aaa = bbbb ? *$
abc / xyz / 1234 / ?*&

OK, in 'doze a line break denotes hit "enter". So I put in the first line hit enter and terminal told me to go jump in a lake.  

So  how do I line break in terminal w/o hitting enter? Or does the line  break mean something else here? Is it all supposed to be one line? And  if so then why did the author break the line?

I need step, by *BABY STEP* instructions on how to perform the basic hardening tasks on my install.

I'd  also appreciate it if you guys could recommend a good front end GUI to  monitor the firewall. I like to know what's going on behind the scenes. I  read in one of the guides that FS is good for basic configuration, but  not so much for monitoring.

I've also read that some of the front  end programs open up more holes than they close. Can you guys suggest a  good list of easy to use front end stuff that will help me lock down my  system with out creating even more headaches?

Also, do I need to lock the host file? And if so how? In 'doze I just change the everybody permission to read only.

And, do I need to create a new "standard user" profile like I in do in 'doze for an added layer of protection? Or is that already taken care of? And if so then how?

BTW I have 10.04LTS

I would like to say, in advance, I truly appreciate you guys taking the time out of your day to help unscramble my noodle.

Thankx.

---

### Post by stevennlv on 2011-07-18
Update,

OK, I figured out how to open "/etc/ssh/sshd_config" with gpedit and I want to add the line "PermitRootLogin no".  But, where do I add it?

And, even though I got the file to open I can't actually edit it? I'm not sure why though?

Also, I found wireshark, but have not dl'ed it yet. Is that a good one to monitor network traffic? My main interest is hits from not allowed inbound trafic.

And, I'm trying to use the console to execute the following:
sudo chown root:admin /bin/su  sudo

So I type that and the hit enter. It then asks for my password. But, when I put it in terminal tells me that there is no such program as sudo?

---

### Post by stevennlv on 2011-07-18
Never mind on most of this. I'm hard headed. I got most of it figured out. Alt-F2 + gksudo gedit + copy and paste + Ubuntu documentaion are now my new best friends! 

But, I still have a few questions:

1) Do I need to "lock" the access permissions in the host file (in other words make read only) like on my 'doze box, and if so then how is it done?

2) Can anyone recommend a good front end network traffic monitor that will alert me to "bad" inbound traffic attempts?

3) I'll come back to the terminal stuff later.


Feel free to jump in any time! :shock:

---

### Post by HiImTye on 2011-07-18
> **stevennlv said:**
> Never mind on most of this. I'm hard headed. I got most of it figured out. Alt-F2 + gksudo gedit + copy and paste + Ubuntu documentaion are now my new best friends! 

But, I still have a few questions:

1) Do I need to "lock" the access permissions in the host file (in other words make read only) like on my 'doze box, and if so then how is it done?

2) Can anyone recommend a good front end network traffic monitor that will alert me to "bad" inbound traffic attempts?

3) I'll come back to the terminal stuff later.


Feel free to jump in any time! :shock:
hosts is in /etc/ so it is 'locked' by default (you need to escalate permissions to access it) - however because it is in a VM and not the primary OS this isn't the case outside of the VM
[here]("http://www.ubuntugeek.com/network-traffic-analyzers-for-ubuntu-system.html")'s a list of network traffic analyzers for Ubuntu

---

### Post by stevennlv on 2011-07-18
> **HiImTye said:**
> hosts is in /etc/ so it is 'locked' by default (you need to escalate permissions to access it)

Cool, thanks for the info.

> **HiImTye said:**
> however because it is in a VM and not the primary OS this isn't the case outside of the VM

Yeah, I already locked the one on the win machine.

  > **HiImTye said:**
>  [here]("http://www.ubuntugeek.com/network-traffic-analyzers-for-ubuntu-system.html")'s a list of network traffic analyzers for Ubuntu
  
Thankx for the info, I'll check them out.

And I figured out the terminal stuff too, turns out the author broke a line (when he should not have) when quoting the U doc's.

Guess it pays to go to the source!

Now if AVAST! will just send that key I think I'll be good.

---

### Post by stevennlv on 2011-07-18
I checked out the list, but I didn't really see what I'm looking for.

I'm not so much interested in detailed network traffic info, but rather being advised when an inbound connection is attempted.

Firestarter will do that. But, I read in one of the guides for noobs (don't remember which one) that I should not be running it all the time because it can open up a potential hole for root access? (Unless I misunderstood?)

Think basically a "windows" type firewall, where I get an alert of some kind to notify me of an inbound connection that violates my firewall rules.

Preferably one that I can set to run at boot without a password. I have a password on my account. I set FS to run at "boot" on the VM. But the boot got really screwy and hung up when I didn't catch the password prompt quickly enough that came up a second time mid-boot for FS.

As it stands now I can manually open FS after boot. But, my wife will be using this a lot too. which means the fewer steps involved the better. She's not the "techie" type at all. It just needs to work so she can get on with facebooking.

---

### Post by coldraven on 2011-07-18
Why Avast? Just install Clam from the Software Centre.
By default in Ubuntu you are not the root administrator, that's why if you want to edit any file that is not in your home directory you have to become root using "sudo" or for a GUI program like Gedit use ```
gksudo gedit
```If you want even less privileges click on the "Power down" icon on the top right of your screen and select "Guest Session".

---

