---
title: "conky not starting"
date: 2012-03-19
forum: General Help
---

### Post by Spewed on 2012-03-19
I'm trying to start conky, but can't seem to get it to start. Everytime I open the terminal and type "conky" I get the following error. 

Conky: invalid configuration file '/home/kolton/.conkyrc'

Conky: missing text block in configuration; exiting
***** Imlib2 Developer Warning ***** :
	This program is calling the Imlib call:

	imlib_context_free();

	With the parameter:

	context

	being NULL. Please fix your program.

I have no idea how to go about fixing it. I went ahead and entered the command "Sudo apt-get purge conky && sudo apt-get conky all"

It removed it and reinstalled, but the error still persists. I read in a thread on here that to fix it you need to add a line that says Text? But I'm not sure in what context I'm to add that line? 

Also, this happens with every conky theme that I download. 

I installed Conky, and created a .conkyrc folder to put the themes in. That is the correct method, right?

---

### Post by Spewed on 2012-03-19
I deleted the ".conkyrc" folder in my home folder, and conky was able to open, but now with the theme that I want.. How do I fix that?

---

### Post by Spewed on 2012-03-19
LOL, I'm a moron and I fixed it already. 

thanks anyway.

---

### Post by stinkeye on 2012-03-19
> **Spewed said:**
> LOL, I'm a moron and I fixed it already. 

thanks anyway.
Hi Spewed,
You can specify any config to use with the **-c** option.
You can name downloaded configs to anything you like
and then run with
```
conky **-c** /path/to/your/conkyconfig
```

---

