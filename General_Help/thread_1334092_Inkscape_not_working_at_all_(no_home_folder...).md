---
title: "Inkscape not working at all (no home folder...)"
date: 2009-11-22
forum: General Help
---

### Post by camaron1 on 2009-11-22
Back in 9.4 at some point Inkscape stopped working. When I upgraded to 9.10 I hoped it would get fixed but it didn't. 

I've installed and reinstalled, purged, install develping version and nothing. I've just noticed though that it doesn't have its own folder in my home folder so I'm guessing that is the problem. Any ideas? Forgot to mention the program actually starts but nothing else.

---

### Post by P4man on 2009-11-22
open a terminal and type

```
inkscape
```

and copy/paste the output here.

---

### Post by camaron1 on 2009-11-22
> **P4man said:**
> open a terminal and type

```
inkscape
```and copy/paste the output here.

No output, it just opens Inksacape

---

### Post by camaron1 on 2009-11-22
I'll reframe the question: how can I force Inkscape make the home folder it would make when it is installed (with plug-ins, conf. files etc)

---

### Post by camaron1 on 2009-11-22
bump!:D

---

### Post by camaron1 on 2009-11-22
One last bump!!

---

### Post by AlphaLexman on 2009-11-22
Post the output of:

```
inkscape --g-fatal-warnings
```

...oh, and one bump per day please. Don't be impatient.

---

### Post by camaron1 on 2009-11-22
> Post the output of:

 	Code:
 	inkscape --g-fatal-warnings 


No output it just opens Inkscape!?

---

### Post by AlphaLexman on 2009-11-22
Ok, try

```
inkscape --without-gui --g-fatal-warnings
```

---

### Post by camaron1 on 2009-11-22
> **AlphaLexman said:**
> Ok, try

```
inkscape --without-gui --g-fatal-warnings
```


**Nothing to do!!**

The above is the actual input, not jocking

---

### Post by mbeach on 2009-11-22
can you post a screen shot of what your inkscape window looks like? When you say it doesn't work, does it crash, or are there no buttons, does your mouse freeze? Can you expand a bit on that?

I have a /home/[user]/.inkscape folder which gets recreated on inkscape launch if I remove it.

Do you have a ~/.inkscape folder?

By the way, I think a bump a day is all that is recommended (not every couple of hours).

edit:
how did you install inkscape?
[http://wiki.inkscape.org/wiki/index.php/CompilingUbuntu](http://wiki.inkscape.org/wiki/index.php/CompilingUbuntu)

---

### Post by camaron1 on 2009-11-22
> **mbeach said:**
> can you post a screen shot of what your inkscape window looks like? When you say it doesn't work, does it crash, or are there no buttons, does your mouse freeze? Can you expand a bit on that?

I have a /home/[user]/.inkscape folder which gets recreated on inkscape launch if I remove it.

Do you have a ~/.inkscape folder?

By the way, I think a bump a day is all that is recommended (not every couple of hours).

edit:
how did you install inkscape?
[http://wiki.inkscape.org/wiki/index.php/CompilingUbuntu](http://wiki.inkscape.org/wiki/index.php/CompilingUbuntu)

I do apologize about the bump, not quite every two hours though I was going to give up on the thread.

As you'll see from the screeshot it looks perfectly normal. What happens is I can't do anything with it, no tool produces anything on the windows, no response.

With regards to **/.inkscape **folder as I pointed out before threre isn't one which I think must be the problem. Installing and re-installing does not create on.

---

### Post by michy99 on 2009-11-22
Do you get anything from these commands?```
ls -ad ~/.inkscape
ls -a ~/.inkscape
```

---

### Post by camaron1 on 2009-11-22
> **michy99 said:**
> Do you get anything from these commands?```
ls -ad ~/.inkscape
ls -a ~/.inkscape
```

For both of them:

**ls: cannot access /home/jorge/.inkscape: No such file or directory**

Which confirms the problem.
Thanks for the interest

---

### Post by michy99 on 2009-11-22
By any chance do you have a .config/inkscape folder?

---

### Post by jocko on 2009-11-22
Inkscape stores it's settings in ~/.config/inkscape, not ~.inkscape.

Try to delete your ~/.config/inkscape folder and start inkscape again to regenerate the default settings.

---

### Post by camaron1 on 2009-11-22
> **michy99 said:**
> By any chance do you have a .config/inkscape folder?


I do indeed, never thought of that one. All subfolders are empty apart from a preferences.xml and a extension-errors.log. I'm posting this as it seem to give the key:

> Extension "XFIG Input" failed to load because a dependency was not met.
Dependency:
  type: executable
  location: path
  string: fig2dev

Extension "DXF Output" failed to load because a dependency was not met.
Dependency:
  type: executable
  location: path
  string: pstoedit
  description: pstoedit must be installed to run; see [http://www.pstoedit.net/pstoedit](http://www.pstoedit.net/pstoedit)

Extension "LaTeX formula" failed to load because a dependency was not met.
Dependency:
  type: executable
  location: path
  string: latex

Extension "LaTeX formula" failed to load because a dependency was not met.
Dependency:
  type: executable
  location: path
  string: dvips

Extension "LaTeX formula" failed to load because a dependency was not met.
Dependency:
  type: executable
  location: path
  string: pstoedit

Extension "Sketch Input" failed to load because a dependency was not met.
Dependency:
  type: executable
  location: path
  string: skconvert

Extension "Dia Input" failed to load because a dependency was not met.
Dependency:
  type: executable
  location: path
  string: dia
  description: In order to import Dia files, Dia itself must be installed.  You can get Dia at [http://live.gnome.org/Dia](http://live.gnome.org/Dia)
This gives me some information, thanks for the pointer

---

### Post by michy99 on 2009-11-22
As an experiment, you could create a new user on your system and see if Inkscape works for that user.

---

### Post by camaron1 on 2009-11-22
> **michy99 said:**
> As an experiment, you could create a new user on your system and see if Inkscape works for that user.


Thanks for your sugestion, I don't really want to do that as it would create issues of its own. I wouldn't solve the problem either.

Looking at log above, what I understand is that some dependencies have not been met. Which are they though? the strings? I would like clarification on this before I start installing all this. Just to have a look I checked on the one called **fig2dev **and the closest I get from synaptic is something called **fig2ps **that brings itself half a tone of its own dependencies. 

Any sugestions?

---

### Post by AlphaLexman on 2009-11-22
Maybe, did you install as root?

Is there a /root/.inkscape/ folder?

if you;

```
sudo inkscape
```

does this make a difference?

---

### Post by camaron1 on 2009-11-22
> **AlphaLexman said:**
> Maybe, did you install as root?

Is there a /root/.inkscape/ folder?

if you;

```
sudo inkscape
```does this make a difference?

Thanks for the suggestion, I just checked that and no, there isn't such a folder either. The command  **sudo inkscape **is not recognized.

---

### Post by camaron1 on 2009-11-22
This is the long [list of dependencies]("http://packages.ubuntu.com/karmic/inkscape") for Inkscape. I've just gone through each of them and I have them all installed. So what is that log file about?

---

### Post by AlphaLexman on 2009-11-22
The log file is just a bunch of file converters you don't have [mine log looks the same].

Something else is wrong. I don't know what. I would make sure you have write permissions, double check the dependencies and the version numbers. Check 64-bit or 32-bit on everything.

I would definitely try adding a user and run inkscape. It will give you some valuable clues. Good luck.

---

### Post by camaron1 on 2009-11-22
> **AlphaLexman said:**
> The log file is just a bunch of file converters you don't have [mine log looks the same].

Something else is wrong. I don't know what. I would make sure you have write permissions, double check the dependencies and the version numbers. Check 64-bit or 32-bit on everything.

I would definitely try adding a user and run inkscape. It will give you some valuable clues. Good luck.

OK this is weird, I have finally followed the suggestion and added a new user without admin. privilegies.  I've logged into this new user and run Inkscape which bloody works fine there. This new user does not have a /.**inkscape** folder either but in this case doesn't seem to matter. Is this a case of some complex-weird permission issue? Does this help anyone to shed some light?

Thanks

---

### Post by camaron1 on 2009-11-22
Update: 

so far i've created 2 new users

-first user without admin. privileges in a different group: inkscape works fine.

-second user with admin privileges in my own group: inkscape works fine.

This is just non-sense

---

### Post by jocko on 2009-11-22
> **camaron1 said:**
> Update: 

so far i've created 2 new users

-first user without admin. privileges in a different group: inkscape works fine.

-second user with admin privileges in my own group: inkscape works fine.

This is just non-sense
Just delete your main users ~/.config/inkscape folder. Next time you start inkscape it will be regenerated with the default settings (which is exactly what happens when you create new users).

---

### Post by camaron1 on 2009-11-22
> Just delete your main users ~/.config/inkscape folder. Next time you start inkscape it will be regenerated with the default settings (which is exactly what happens when you create new users).

Thanks jocko, this has finally fixed the issue, I can't believe I didn't thinks of this. It's been a long Sunday trying to get this sorted. I still wonder what was in the conf. file that would render the program useless. I guess I won't find out. 

Thanks again.

---

