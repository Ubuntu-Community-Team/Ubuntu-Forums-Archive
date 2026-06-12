---
title: "ddrescue help"
date: 2012-04-15
forum: General Help
---

### Post by Fafnr on 2012-04-15
Hey all,

I'm sorry if this is the wrong forum for this, but I don't know where else to ask!

I'm trying to recover a laptop for a friend of mine, and after som searching came upon a Ubuntu Remix called Boot Med.

It recommended using ddrescue in the following manner:

sudo dd_rescue /dev/sdxx /media/Elements/image.dd

so I ran the equivalet of that with the correct device and some other output destination.

I started the rescue friday night and it's still (!!!) running!

So, I have a few questions:

1) I didn't specifically ask for a logfile... Does it make one anyone so I can pause and resume the recovery?
2) Is it normal it takes this long?! After about 290gb was recovered it suddenly hit the error portion, and it's been on "bad block" for 24 hours, with only aboyt 2900 errors and 1438.5k errxfer!?
3) Can I mount the partial .dd file and try to recover what's on there?
4) Basically - can I do ANYTHING to speed this up?

Thanks so much in advance!

---

### Post by GnL on 2012-05-02
Did you find any answers to your questions? I've recovered 10 gb out of a 250 gb disc but now it has been stuck on faulty sectors for a week!

/GnL

---

### Post by Fafnr on 2012-05-02
I never did find a way of speeding it up / suspending-restarting it, however I did take a copy of the partial file, renamed .dmg and mounted it in OS X which worked fine!
So I guess you can do the same thing via built-in linux commands.

And, yes, it did take forever. My recovery ran almost 3 weeks, day in, day out!!

---

### Post by GnL on 2012-05-02
OK, thanks. I guess I just have to be patient then... ;)

---

