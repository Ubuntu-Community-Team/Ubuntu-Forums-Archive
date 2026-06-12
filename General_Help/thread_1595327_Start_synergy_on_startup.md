---
title: "Start synergy on startup"
date: 2010-10-13
forum: General Help
---

### Post by P4man on 2010-10-13
Hi,
Im trying to run synergy on startup. This works fine on the client, but it wont start automatically on the server. I put this line in an entry in startup applications:

```
synergys -c ~/.quicksynergy/synergy.conf
```

Which works fine from the commandline, but not from startup apps. Synergy server simply doesnt start. I did some googling and found I might need a delay so I tried

```
sleep 10s; synergys -c ~/.quicksynergy/synergy.conf
```

but still no dice. There has to be something obvious Im missing?

---

### Post by Grenage on 2010-10-13
My synergy server simply runs the following code, as a startup application:

```
synergys --config /home/grenage/.synergy.conf
```

I know that's not particularly helpful, since it's nearly a "it works here".  Have you considered adding it as a cron job?

---

### Post by P4man on 2010-10-13
Well, Im stumped. Against my own better judgement I changed whats different in your line, so I put an absolute path to the config file, which I hid and copied to my homefolder, and I changed -c into --config and now for some reason it works lol.

edit: its the tilde that did it. For some reason that doesnt work, if I replace it with an absolute path, it works fine also with the rest of my original settings.

thanks again.

---

### Post by Grenage on 2010-10-13
Odd, I might consider that a bug for launchpad.  I can't see why the tilde should cause a problem.

---

### Post by P4man on 2010-10-13
can you perhaps test on your machine to exclude the possibility I did something else wrong?

---

### Post by Grenage on 2010-10-13
Yup.  I'm not in the office at the moment, but I'll test it when I am, then post back.

---

### Post by Grenage on 2010-10-15
I can confirm that it does not work here, not with the home folder 'shortcut'.  I added it to my user crontab, but that didn't work either.

---

### Post by P4man on 2010-10-15
Did another test. In startup applications I created an entry for

```
gedit ~/Desktop/test
```

It starts gedit and opens a document test with the following path:

```
gedit ~/~/Desktop/test
```

Ill file a bug report.

---

### Post by Grenage on 2010-10-15
Good deducing!

I attempted something similar with an echo command, using 'startup applications':

echo testing123 > /home/grenage/static

echo testing123 > ~/dynamic

Neither of them worked, so I dropped it there.

---

### Post by aoberoi on 2010-12-06
great stuff guys! i had the same issue and your investigation fixed the issue for me.

one thing i'd like to ask though. i'm not sure how the whole startup once the gnome login has occurred works, but while i was trying to figure out how to get around this i tried adding a couple lines to my ~/.xsession file (which i created and made executable).

```
/usr/bin/killall synergys
sleep 1
/usr/bin/synergys --config /home/aoberoi/.synergy/synergy.conf
```

this did NOT work. i used the exact same command in the Startup Applications provided by Gnome and it DID work. so my question is, what's the point of this .xsession file? does it only get run under other circumstances? what circumstances might those be? i'm sure the people of this forum have better things to do than explain the details to me so a good link to a reference that describes the use in relation to Ubuntu and Gnome would be great!

---

