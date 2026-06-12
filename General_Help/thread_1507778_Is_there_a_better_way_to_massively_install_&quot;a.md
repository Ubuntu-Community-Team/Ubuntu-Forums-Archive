---
title: "Is there a better way to massively install &quot;all&quot; packages?"
date: 2010-06-12
forum: General Help
---

### Post by DThurman on 2010-06-12
I find that 'Software Center' simply is to slow and cumbersome
to use and it often gets slower and slower as more package are
installed and eventually it hangs, so presently, I dumped all
available deb packages to a file, painstakingly edited out what
I do not want installed and in a bash script.  The problem is
encountering packages that wants to configure itself with user
responses, and of course it was not possible to do inside of
a script and so the entire process hangs.  I have to kill off
the dpkg that was lanuched, kill the script, and remove the
package from the list, manually install the offending package
and restart the whole shing-bang.  This is too painful...

What I'd like to know if there is a better way?

It would be nice if there was something like a yum groupinstall
debian equivalent so that I could install say, "development",
"accessories". and so on, to make the installing process quicker.

Any pointers?

---

### Post by clhsharky on 2010-06-12
DThurman

Synaptic Package Manager is the best way I know to control packages.

Software Center was designed for noobs, AFAIC.

Sharky

---

### Post by tgm4883 on 2010-06-12
yea synaptic works great

If you really want to use command line then

```
apt-get install package1 package2 package3 package4 etc
```

---

### Post by DThurman on 2010-06-12
> **tgm4883 said:**
> yea synaptic works great

If you really want to use command line then

```
apt-get install package1 package2 package3 package4 etc
```

Yeah, but does CLI apt-get support group-names?
From what I found, it's a no. What a pain...

So, I guess in the end, scripts or synaptic is
the only thing available.

---

### Post by geirha on 2010-06-12
By group you mean section? like for instance the games section?
With aptitude you can list all packages in a section with e.g.
```
aptitude search '~s games'
```
You can further choose only packages that are not installed (!~i), and also format the output to only include the package names.
```
aptitude -F "%?p" search '!~i ~s games'
```
And then, of course, pass that list as args to apt-get/aptitude install.

See /usr/share/doc/aptitude/README

EDIT: Actually, you can use those patterns for install as well.
```
aptitude install '!~i ~s games'
```

---

### Post by BurningSludge on 2010-06-12
[FONT=Comic Sans MS][SIZE=3]I like to use the Synaptic Package Manager for installations because it seems faster and more stable than the Ubuntu Software Center, at least to me.
[/SIZE][/FONT]

---

### Post by jerome1232 on 2010-06-12
Just btw you can't install them all, there are conflicts and such that will prevent x package if you have y package installed.

---

### Post by DThurman on 2010-06-12
> **geirha said:**
> By group you mean section? like for instance the games section?
With aptitude you can list all packages in a section with e.g.
```
aptitude search '~s games'
```
You can further choose only packages that are not installed (!~i), and also format the output to only include the package names.
```
aptitude -F "%?p" search '!~i ~s games'
```
And then, of course, pass that list as args to apt-get/aptitude install.

See /usr/share/doc/aptitude/README

EDIT: Actually, you can use those patterns for install as well.
```
aptitude install '!~i ~s games'
```

Well now!  Maybe you have something here?

How did you know what the section (group) names are beforehand?

I'll try it out!
Thanks!

---

### Post by DThurman on 2010-06-12
> **jerome1232 said:**
> Just btw you can't install them all, there are conflicts and such that will prevent x package if you have y package installed.

Yes, of course!  But you can get around it when you encounter
them, right? Once you have a "list" then you can use that list
for installing other systems the same way, at least that is why
I am doing it.

---

### Post by geirha on 2010-06-12
> **DThurman said:**
> 
How did you know what the section (group) names are beforehand?


That I don't know. I just did aptitude show on a game package. «aptitude -F %s search . | sort -u» should give you a list of all the sections, though there's probably a more efficient way to get that list.

---

### Post by inameiname on 2010-06-12
Personally, I just install most through the terminal, using the already suggested method of:

sudo aptitude package1 package2 package3 package4 ...

I install two gigs worth that way and it works just fine. That is, of course, after I've added all the repos that I use.

---

### Post by tgm4883 on 2010-06-12
Why would you want to install all packages?

---

### Post by garvinrick4 on 2010-06-12
It really takes so little time to do a set-up in Ubuntu. To run your command line and while that is loading set up your panels and menus. From top to bottom you got 20 or 30 minutes. Or this second way below which I ran across one day. I quess everyone wants their own way of installing, so thats OK. Everyone likes to do their own thing.


                                 The second way of doing this doesn't create a large package, but rather a small list of apps that can be used to direct your computer to what to reinstall. This requires no installation of anything to actually run the command, but does require an internet connection. Now, this creates a list of everything, even standard system stuff, so don't get freaked out if theres stuff you've never seen on it before. Any overlap with standard stuff works itself out, it won't reinstall or duplicate things. The really nice thing about this method is that you can manually add or subtract stuff from the list.
 Found this in these Forums at one time or another.

To do this, run this command:
 
[LIST]
[*][FONT=inherit]sudo dpkg --get-selections >     installedsoftware[/FONT]
[/LIST]
 [FONT=inherit]Then, all you have to do is copy that folder over to the home f[/FONT]older of the next computer and/or after the clean install, and then run:
 
[LIST]
[*]sudo dpkg --set-selections < installedsoftware
[/LIST]
 Needs internet connection.

---

### Post by tgalati4 on 2010-06-12
Be aware that when you try to install everything, time slows down such that you are never able to finish.

---

### Post by garvinrick4 on 2010-06-13
> **tgalati4 said:**
> Be aware that when you try to install everything, time slows down such that you are never able to finish. I just saw the "all" packages I hope OP did not mean all of the packages available in repositories. Just all the packages they use in an install. GZZZ all the packages!!!!! That is a bunch. Most likely on a 56k modem, that would take a bit of time, just a bit.

---

### Post by tom.swartz07 on 2010-06-13
> **tgalati4 said:**
> Be aware that when you try to install everything, time slows down such that you are never able to finish.

Its like approaching the speed of light, you cant actually slow down time and gain mass.
:P

---

### Post by DThurman on 2010-06-14
> **garvinrick4 said:**
> I just saw the "all" packages I hope OP did not mean all of the packages available in repositories. Just all the packages they use in an install. GZZZ all the packages!!!!! That is a bunch. Most likely on a 56k modem, that would take a bit of time, just a bit.

Yup!  "all" is in quotes for a reason! :P

The OP (that's me!) does not intend to install ALL
packages, just a LOT of the ones wanted, and to be
"cloned" to other systems.  Gotta watch those quotes :lol:

Also, the above suggestion about using get/set-selections
is a good idea because one could setup a system as a
snapshot and saved as original-settings just before adding
new packages, and when the "fit hits the shan", then one
could then take a second snapshot and "compare notes"?

As it is, now I have to figure out what the heck happened
to my network-manager, and also why autoremove wants to
blow away my bind9... rats.  Had I saved a snapshot, I
would at least do a diff and see what might have been
added to cause this problem...

All useful suggestions & thanks.

---

