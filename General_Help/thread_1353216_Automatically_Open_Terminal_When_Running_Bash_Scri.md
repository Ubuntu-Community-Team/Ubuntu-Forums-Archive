---
title: "Automatically Open Terminal When Running Bash Script"
date: 2009-12-12
forum: General Help
---

### Post by tacantara on 2009-12-12
I designed a bash script that will install the ubuntu-restricted-extras and flashplugin-nonfree, for whenever I do a fresh install of Ubuntu.  I also designed scripts that will run Ubuntuzilla for updating Firefox and Thunderbird.  To get the script to run in terminal, I have to right-click the script file, and select the option to open in terminal.  Is there a way I can reduce that to a single step, i.e. a launcher that automatically opens the script in a terminal?  I've tried to look it up on Google, but I haven't found any useful advice (perhaps I'm not executing the search properly).

The scripts execute flawlessly when I right-click and opt to run in terminal.  In fact, I just installed Lucid Lynx (Alpha) on a separate partition on my laptop, and used the restricted extras/flash script to install those packages without flaw.

---

### Post by kaibob on 2009-12-12
> **tacantara said:**
> Is there a way I can reduce that to a single step, i.e. a launcher that automatically opens the script in a terminal?

The following should work. The bash at the end of the command is to insure that gnome-terminal remains open after the shell script has executed. 

```
gnome-terminal --execute bash -c "scriptname ; bash"
```

---

### Post by tacantara on 2009-12-12
> **kaibob said:**
> The following should work. The bash at the end of the command is to insure that gnome-terminal remains open after the shell script has executed. 

```
gnome-terminal --execute bash -c "scriptname ; bash"
```

That did the trick :)  This was much easier than I expected it to be.  Thanks for the tip!

---

### Post by coolblood12 on 2010-11-11
> **tacantara said:**
> That did the trick :)  This was much easier than I expected it to be.  Thanks for the tip!

Hi where I have to put this command?

I try to put in the first line of code in the bash but don't function.

and try in the Properties/Open with press the Add button but still get the message Run in Terminal or Display. 

Please HEEEEEEEEEEEEELP

---

### Post by coolblood12 on 2010-11-11
> **tacantara said:**
> That did the trick :)  This was much easier than I expected it to be.  Thanks for the tip!

Hi where I have to put this command?

I try to put in the first line of code in the bash but don't function.

and try in the Properties/Open with press the Add button but still get the message Run in Terminal or Display. 

Please HEEEEEEEEEEEEELP.

---

### Post by coolblood12 on 2010-11-11
Hi where I have to put this command?

I try to put in the first line of code in the bash but don't function.

and try in the Properties/Open with press the Add button but still get the message Run in Terminal or Display. 

Please HEEEEEEEEEEEEELP...

---

