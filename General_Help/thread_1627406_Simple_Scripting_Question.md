---
title: "Simple Scripting Question"
date: 2010-11-21
forum: General Help
---

### Post by hantechbl on 2010-11-21
I am making a Minecraft installer script, I know the basics, but after looking at all the tutorials I could find, I realized I have no Idea how to add options, I want to add a yes no question and have the action vary apon what option is chosen so like: If Y then wget [http://minecraft.net/x/x](http://minecraft.net/x/x)
If N goto a diffrent step
How would I go about doing this?

---

### Post by zitch on 2010-11-21
If you're using BASH, there are a few options;

[9.1 Using select to make simple menus]("http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-9.html#ss9.1")
[10.1 Reading user input with read]("http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-10.html#ss10.1")

If you're using something else (including possibly SH; I'm sure "read" is available, but not sure if select is in SH) You'll have to find the way to get user input in that language.

Please note that I haven't messed with input in BASH scripts before.  The most I have done is checking for command-line arguments, and that was only once.

---

