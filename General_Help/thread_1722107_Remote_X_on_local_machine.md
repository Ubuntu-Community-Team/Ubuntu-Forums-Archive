---
title: "Remote X on local machine"
date: 2011-04-05
forum: General Help
---

### Post by jamesisin on 2011-04-05
I've wanted to try serving GUI applications to a local machine for some time now.  I found this howto and decided to give it a shot:

```
http://www.csci.csusb.edu/****/samples/remote.html
```

I have confirmed that remote.local is added to xhost on my little lappy here.  However, when I try to run my command I get an error:

```
$ DISPLAY=mylappy.local:0.0 gedit examples.desktop

(gedit:2418): Gtk-WARNING **: cannot open display: mylappy.local:0.0
```

Ideas?

---

### Post by seawolf167 on 2011-04-05
The website provided doesn't load anything.

Any reason that X forwarding over SSH wouldn't work?

Something like:

```
ssh -l *username *-p *portnumber *-c blowfish -C -X *ip.address.goes.here*
```

---

### Post by jamesisin on 2011-04-05
Didn't notice that.  The article is by a guy named Richard.  The usual nickname for a guy named Richard is ****.  **** is also a pet-name for one's *****.  Can't have that displayed where children might see it...

Anyway fix that and the URL should work fine for you.

The method you suggest...  let me know if I misunderstand things here.  Your method runs X on the server machine while the method linked above runs X on the local machine (thus reducing overhead on the remote machine).

---

### Post by seawolf167 on 2011-04-05
The ssh X11 forwarding command I posted previously would run the X server on the local machine. For example, if you wanted to forward X to a Windows machine, you'd need to install a program like [Xming ]("http://www.straightrunning.com/XmingNotes/")which would be able to display forwarded X11 information from the server machine.

The link you posted looks like essentially the same thing - just that it's a little outdated as you don't usually need to specify all the provided variables manually on the standard Ubuntu distro.

---

### Post by jamesisin on 2011-04-05
Adding the xhost is still required?

---

### Post by seawolf167 on 2011-04-05
Nope - all I do to forward X11 to my computer from school/work/home is edit the parameters on the command I posted above. You can test it with something like

```
xclock
```

after you login via ssh

You *may* need to change your $DISPLAY variable, but only rarely do I have to do that.

---

### Post by jamesisin on 2011-04-05
Well, I tried both of these:

```
ssh -f -C there.local gedit examples.desktop

DISPLAY="here.local:0.0" ssh -f -C there.local gedit examples.desktop
```

They both generated the same basic error:

```
(gedit:1773): Gtk-WARNING **: cannot open display:
```

Also, from the remote machine:

```
me@there:~$ xclock
Error: Can't open display: 
me@there:~$ DISPLAY=here:0.0 xclock
Error: Can't open display: here:0.0
```

---

### Post by seawolf167 on 2011-04-05
First thing I'd check is ensuring that you have "X11Forwarding" set to "yes" in /etc/ssh/sshd_config

Then restart ssh

```
sudo service ssh restart
```

If that doesn't work, see the post [here]("http://www.myiphoneadventure.com/tag/ubuntu") since you may be running into a known bug

---

### Post by jamesisin on 2011-04-05
Thanks.  I tried adding the -4 option and restarting ssh to no avail.  Also I confirmed that X11 forwarding is enabled.  (Both on the remote machine.)

---

### Post by jamesisin on 2011-04-05
I love those days when I wake up in full idiot regalia.  If you take a look at the commands I posted above there is a notoriously lacking -X.  Thank you for also not noticing it as it makes me feel less doltish.  Correcting that, oddly enough, corrects the problem and I am able to get ssh to draw X over the tunnel.  Thanks for humoring me in my bumbling.

---

### Post by lithopsian on 2011-04-05
ssh -X is one of the simplest ways to do this but it is far from perfect and performance can be pretty poor.  I'm sure there are better tools out there.  Certainly there are commercial tools but I don't know about open source.

---

### Post by seawolf167 on 2011-04-05
Hehe, glad you got it working! :) I know I've made mistakes like that *plenty of times!*

---

### Post by jamesisin on 2011-04-05
> **lithopsian said:**
> ...performance can be pretty poor.

Seems ok and the here machine is a Dell Mini (Atom z520 @1.33GHz and 1GB RAM) with both machines connected via wireless.

---

### Post by seawolf167 on 2011-04-05
> **lithopsian said:**
> ssh -X is one of the simplest ways to do this but it is far from perfect and performance can be pretty poor.

The '-C' switch adds compression to the connection - it is very useful for running over WAN or on slow networks. If you are LAN only and everything is running smoothly, you can easily leave this switch off and save a little CPU overhead.

On the other side, if you need a higher compression rate for very slow networks you can change the compression level in the range of 1-9 (1=fast & small compression, 9=slow & large compression)

Its been a while, but I think the file you edit (or create) is

```
nano ~/.ssh/config
```

then change/add

```
Compression yes
CompressionLevel 1-9
```

---

