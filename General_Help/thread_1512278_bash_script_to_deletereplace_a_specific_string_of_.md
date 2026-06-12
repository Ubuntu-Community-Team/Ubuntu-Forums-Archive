---
title: "bash script to delete/replace a specific string of text"
date: 2010-06-17
forum: General Help
---

### Post by angry_johnnie on 2010-06-17
What i want to do is pretty simple.

I want to uncomment every line that begins with "deb" (except for deb cdrom) in /etc/apt/sources.list.

I know how to do this through system > administration > software sources.

I know I can gksu gedit /etc/apt/sources.list.

I'd rather not do it that way.

I'd rather have a script do it.  It's less work, less typing, less clicking, and would work the same on every ubuntu version.

I'm thinking sed, grep, awk, or something, but I'm no expert.

Any ideas?

---

### Post by mobilediesel on 2010-06-18
> **angry_johnnie said:**
> What i want to do is pretty simple.

I want to uncomment every line that begins with "deb" (except for deb cdrom) in /etc/apt/sources.list.

I know how to do this through system > administration > software sources.

I know I can gksu gedit /etc/apt/sources.list.

I'd rather not do it that way.

I'd rather have a script do it.  It's less work, less typing, less clicking, and would work the same on every ubuntu version.

I'm thinking sed, grep, awk, or something, but I'm no expert.

Any ideas?

Easy enough with sed:
```
sudo sed -i 's/\(^# \)\(deb.[^c]\)/\2/' /etc/apt/sources.list
```
but first try this to make sure it changes the lines you want:
```
sed -n 's/\(^# \)\(deb.[^c]\)/\2/p' /etc/apt/sources.list
```

---

### Post by angry_johnnie on 2010-06-18
Thank you much for your reply.

The code however, isn't quite right.

if i run

```
sudo sed -i 's/\(^# \)\(deb.[^c]\)/\2/' /etc/apt/sources.list
```

it doesn't change anything.

if i remove the dot after deb

```
sudo sed -i 's/\(^# \)\(deb[^c]\)/\2/' /etc/apt/sources.list
```

it only uncomments the deb cdrom line. :p

i want to uncomment everything but that line. :)

if i had the slightest idea of what all these little symbols do (all the slashes, apostrophes and whatnot) i'd edit it further.  but my bash scripting skills aren't all that advanced.

the reason i want this is i've written a script, from which a user can choose to install, or not, some apps.  the list of apps includes only stuff that is usually installed (in this house, at least).  things like restricted-extras, frozen-bubble, soundconverter, googleearth, etc.  

i don't like/trust upgrades.  i'd rather do a fresh install every time.  and every time i have to install the same things for everyone in this house.  sometimes i forget i have to install something for someone.  and, they'll bug me later about it:  "how do i install xyz?"

editing sources.list, updating, and installing software ain't all that straight forward for quite everyone in the house.

so i wrote this script.  next time they ask how do i install xyz?  i'll just tell them to double click on the script.  with it, i don't even have to install anything.  i can leave them with a fresh, vanilla install, and the script, so they can install what they think they'll use.

that makes things easier for me, and for everyone else in the house as well.

the part where the user chooses software if pretty simple, and i've already got it.  i've used zenity --list --checklist to make it as easy and straight forward as possible.  i don't have a problem with readable code.  :p  my nightmares begin with the little symbols.

so, i've added the medibuntu repo to the script (because it's a one liner provided by medibuntu :p), but i still don't know how to uncomment the other repositories, without actually editing sources list, and without going through system > administration > software sources.

so i guess that leaves us back where we started.  :)  how do i do that?

attached is a sample of the script i'm writing.




on a side note, if i run your second bit of code:
```

sed -n 's/\(^# \)\(deb.[^c]\)/\2/p' /etc/apt/sources.list
```

it does print the desired output, but the first bit of code, doesn't work.

---

### Post by angry_johnnie on 2010-06-18
got it!

your code does work.

it was just a little detail.

to test it, i commented out the lines like this:

#deb yadda yadda

they are usually commented out like this:

# deb yadda yadda

so, i noticed your code has this:

(^# \)

and it just seemed logical.  you are uncommenting # deb yadda yadda, and not #deb yadda yadda.

so i tried it with (^#\), and it works.

then i commented out the lines the way they normally are (# deb yadda yadda), and then tried your original code:  (^# \).

and it does work. :)

i've been reading man sed.  it's not very explicit, though.  might try looking somewhere else for futher details.

thank you much.
i think i just learned something :p


attached is the final version, if anyone's interested.

---

### Post by mobilediesel on 2010-06-18
> **angry_johnnie said:**
> got it!

your code does work.

it was just a little detail.

to test it, i commented out the lines like this:

#deb yadda yadda

they are usually commented out like this:

# deb yadda yadda

so, i noticed your code has this:

(^# \)

and it just seemed logical.  you are uncommenting # deb yadda yadda, and not #deb yadda yadda.

so i tried it with (^#\), and it works.

then i commented out the lines the way they normally are (# deb yadda yadda), and then tried your original code:  (^# \).

and it does work. :)

i've been reading man sed.  it's not very explicit, though.  might try looking somewhere else for futher details.

thank you much.
i think i just learned something :p


attached is the final version, if anyone's interested.

I did it that way because I've noticed the lines usually are commented with the # and a space before deb.

This would handle with or without the space:
```
sudo sed -i 's/\(^# *\)\(deb.[^c]\)/\2/' /etc/apt/sources.list
```
The ***** I added tells it "zero or more spaces" so it will uncomment either of these lines:
```
# deb blah blah
#deb blah blah
```
and still skip the cdrom line.

---

### Post by angry_johnnie on 2010-06-18
> **mobilediesel said:**
> 
```
sudo sed -i 's/\(^# *\)\(deb.[^c]\)/\2/' /etc/apt/sources.list
```
The ***** I added tells it "zero or more spaces"... 


Now, that's an even better approach! :)
Thank you, one more time!

I better start learning sed.  Seems pretty darn useful! :p

---

### Post by WorMzy on 2010-06-18
Just be careful when using it in that sort of scenario, make a backup of system files before you run sudo sed <anything> on them, just in case you've made a mistake anywhere.

---

### Post by angry_johnnie on 2010-06-18
> **WorMzy said:**
> make a backup of system files before you run sudo sed <anything> on them...


You're absolutely right about that :)
nothing as easy, quick, and useful, as backing up a system file.
I'll incorporate that into the script, before it touches anything ;)


Attached is the final version.

I included a little bit more code, to look for a backup of sources.list, and compare it, if found, to the current version of sources.list.  If there is a difference, the script will create a new backup.  otherwise, it will keep current backup and continue with no further changes.

---

### Post by mobilediesel on 2010-06-19
> **WorMzy said:**
> Just be careful when using it in that sort of scenario, make a backup of system files before you run sudo sed <anything> on them, just in case you've made a mistake anywhere.

> **angry_johnnie said:**
> You're absolutely right about that :)
nothing as easy, quick, and useful, as backing up a system file.
I'll incorporate that into the script, before it touches anything ;)
Attached is the final version.

I included a little bit more code, to look for a backup of sources.list, and compare it, if found, to the current version of sources.list.  If there is a difference, the script will create a new backup.  otherwise, it will keep current backup and continue with no further changes.

Yeah I should have mentioned backing up. I used to get a newsletter where people would ask computer questions. The first response to crashes was usually along the lines of "You have a working backup, right?"


The lines for the diff and backup can be written like this:
```
sudo diff -i -b -B -q /etc/apt/sources.list{,.bak}
sudo cp /etc/apt/sources.list{,.bak}
```
It wont speed up execution time or anything but any time I can save myself some typing by making the computer do it, that's what I do. :D

I also use [Autokey]("http://code.google.com/p/autokey") to do some text-expansion.

---

