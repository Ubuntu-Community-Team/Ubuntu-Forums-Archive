---
title: "Bash Script &quot;command not found&quot; Error, Please Help!"
date: 2010-03-12
forum: General Help
---

### Post by lonewaster on 2010-03-12
Hi there!
I am trying to write some new scripts for in my personal /bin/ folder, but I keep getting the following error-
```

billy@billy-laptop:~/bin$ encrypt
: command not foundrypt: line 2: clear

```

Now, I have a few other scripts- ALL of which use the ***clear*** command at some point. It just seems that any **new** scripts I write are giving me these errors, all of which are of a similar nature.
The script I am currently working on is **encrypt** - which automates gpg encryption.

Can someone help me please?
It **is not** anything to do with the actual script, but more the command, because if I make a fresh, new script and just use the ***clear*** command- it gives me a similar error.
This happens even though all my previous scripts work fine.
Please help!

**!!! VIVA LA LINUX !!!**

*lonewaster*

---

### Post by lonewaster on 2010-03-12
It turns out that if i RETYPE the clear command in a fresh script then it works...

EDIT- Seems that if I type the script out again that it is going to work...

Does WINDOWS notepad save text files in an inappropriate format for bash scripting??

Could this problem be because i initially typed the script on a windows xp system and then emailed it to myself?

---

### Post by cjhabs on 2010-03-12
> **lonewaster said:**
> It turns out that if i RETYPE the clear command in a fresh script then it works...

EDIT- Seems that if I type the script out again that it is going to work...

Does WINDOWS notepad save text files in an inappropriate format for bash scripting??

Could this problem be because i initially typed the script on a windows xp system and then emailed it to myself?

Yes, this is probably a line end issue due to the different codes that DOS and Linux use (and Mac).
You can grab this:
sudo apt-get install tofrodos

then run your scripts through the dos2unix program - that will fix it.

---

### Post by DaithiF on 2010-03-12
yes, line endings differ between windows and {u,li}nux.
linux = a newline character
windows = a carriage return character followed by a newline

you can convert between the two using dos2unix / unix2dos (install the tofrodos package for these)

or you can do it manually, eg:
```
sed 's/\r$//' dosfile > unixfile

```

---

### Post by lonewaster on 2010-03-12
Thanks guys.
Seems really trivial and a bit of a silly question now...and I probably should have thought harder before posting...but thanks all the same.
***tofrodos **is installing now =)*

---

