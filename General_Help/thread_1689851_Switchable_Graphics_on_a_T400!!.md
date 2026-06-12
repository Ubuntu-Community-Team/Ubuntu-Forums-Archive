---
title: "Switchable Graphics on a T400!!"
date: 2011-02-17
forum: General Help
---

### Post by lordadi on 2011-02-17
Hi,

I've just had someone ask for help in getting switchable graphics working on a T400 and I thought I'd share it with the forums so that it can be of use to many more people.

Firstly, I must credit my source: [Digitizor]("http://digitizor.com/2010/10/09/how-to-switch-between-gpu-in-ubuntu-10-10/"). Ok great.

Now, you can just follow through with what they've said on their page but I'd like to offer some notes that may be relevant as you go along.

Some things of interest/relevant considerations:
[LIST=1]
[*]You can **ONLY** use the OPENSOURCE AMD driver. You **CANNOT** use fglrx.
[*]Using this method WILL cause X to restart - so save your work. Don't say you weren't warned.
[*]This is NOT auto switching through acpi as you are used to under windows. This is on-demand (as in, the user demands it).
[/LIST]

Also, you should realize that this method *can* cause X to lock up - I've never had it happen, but it has been an issue on a pal's T400, he needs to reboot when it happens. So if you do something that means you can't let your T400 reboot for periods on end, be sure to think twice.

As far as I am aware, you need a 2.6.35 kernel so Ubuntu with that should do. However, this is the point where I am no longer able to offer any advice as I don't understand much about kernel level stuff. My advice is that if you really want this, use 10.10 as that was designed for/with 2.6.35.

Oh, and I've tested this on a T400 with 10.10 x64. Works brilliantly.

If you have questions, you can ask but I can't promise I'll be useful:)

---

