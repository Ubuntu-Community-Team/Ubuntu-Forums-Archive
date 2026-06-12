---
title: "7 problems/questions"
date: 2010-01-12
forum: General Help
---

### Post by FreezWay on 2010-01-12
[s]1. How can I create a xxxxx.tar.bz2 of my /home/user without including things like .wine and .electricsheep and other things that are really big and take a while to compress? When I run 
```
$sudo tar -cjf backup.tar.bz2 /home/user
```
it does all of it. (yes I know about things like sbackup, but I'm trying to be more fluent in the cli)[/s]
Done

2. Nexuiz issues
a. Sometimes (at completely random times) it starts lagging a lot. If I press [ctrl] [alt] [F1] and the [ctrl] [alt] [F7] it stops, but its a pain.
b. This has only happened twice, but it has randomly quit.

3. Warcraft III (under wine)
I'm having the same problem as #2b

4. Login, I get a
> The application "Do" (i'm guessing gnome-do) (/usr/bin/mono) want to access the default keyring but it is locked.
message and I have to type in my password (I autologin b/c I'm the only user)

5. Ocasionly the panel (it autohides) will invert from it regular activity and hide when I want to use it and unhide when I dont, is this a bug? how do I fix it?

6. How can I change all of my 4 cores to 2.33GHz at once without having 4 cpu scaling icons?

7. Flash is really choppy, see specs in sig for my hardware. This site is a real chopper! [http://www.experiencetheplanets.com/](http://www.experiencetheplanets.com/) 
Thats it for now.

---

### Post by mocoloco on 2010-01-12
For Warcraft III there's a registry key to allow it to use OpenGL I guess instead of Direct3d.  If you want first backup your registry file with 
```
cp ~/.wine/user.reg ~/.wine/user.bak
```
Then copy this into a file, say war3opengl.reg ```
[HKEY_CURRENT_USER\Software\Blizzard Entertainment\Warcraft III]
Gfx OpenGL"="1"
```

then run ```
regedit war3opengo.reg
``` to add it to wine's registry.  That really helped for speed on my install.

---

### Post by FreezWay on 2010-01-12
i run it with the -opengl flag.

---

### Post by JC Cheloven on 2010-01-12
> **FreezWay said:**
> 6. How can I change all of my 4 cores to 2.33GHz at once without having 4 cpu scaling icons? 

Right-click on a panel (maybe the upper one)
Select add to panel
Search for "CPU frequency monitor", and add it.

This allows to choose between several modes, or several fixed freqs. I think it's what you want.

---

### Post by FreezWay on 2010-01-12
I have that, but it only seems to apply it to one cpu at a time.

---

### Post by cenzorrll on 2010-01-12
> **FreezWay said:**
> 1. How can I create a xxxxx.tar.bz2 of my /home/user without including things like .wine and .electricsheep and other things that are really big and take a while to compress? When I run 
```
$sudo tar -cjf backup.tar.bz2 /home/user
```
it does all of it. (yes I know about things like sbackup, but I'm trying to be more fluent in the cli)

if you add --exclude=xxx it will not add those files/folder to the archive. so it would look like this:

```
$sudo tar -cjf backup.tar.bz2 --exclude=filename --exclude=folder /home/user
```

i would also add the options v and p also to preserve permissions and tell you what's going on in case there's an error, so it would look like:

```
sudo tar -cvpjf
```

the man pages are also helpful in case you want to learn more

---

### Post by FreezWay on 2010-01-18
sweet got that to work. turns out i was cfj not cjf.

anyway, anyone got a clue about the other 7?

---

### Post by cenzorrll on 2010-01-19
as for the flash issue, that's adobe's problem i believe. from what i've read on these forums the 64bit version is *less* choppy than the 32bit version, but it has something to do with graphics acceleration and integration, etc, blah blah, techy talk not many people care to understand.

but that's just what i've heard, so don't take any of that for facts  (you know how rumors are), so i think we'll have to sit it out for a little bit until someone figures it out.

---

### Post by FreezWay on 2010-01-19
hmmm... adobe needs to get their act together. at least youtube plays fine.

---

