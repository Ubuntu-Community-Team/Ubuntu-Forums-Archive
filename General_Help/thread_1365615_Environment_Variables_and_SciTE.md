---
title: "Environment Variables and SciTE"
date: 2009-12-27
forum: General Help
---

### Post by invisisci on 2009-12-27
Hi all,

I'm new to the forum (and Ubuntu, although I have a some general Linux experience)! Any help with this appreciated - my guess is that it's a pretty simple fix if I only knew what to do =]

**Problem:**
Some commands won't work in SciTE. I think it's because SciTE doesn't seem to have all of my environment variables set, but I don't know how to change that! I've done a fair bit of googling/searching this forum, and found tantalizing hints but nothing that has allowed me to fix the problem.

**Details:**

[LIST]
[*]Here's an example of a command that doesn't work: [FONT=Courier New]command.build.*.as=mxmlc $(FileNameExt)[/FONT]
[LIST]
[*]mxmlc exists on my system (it's Adobe's compiler for action script) in /etc/FlexBuilder/bin/
[*]I can invoke mxmlc correctly from a terminal just by typing "mxmlc"
[LIST]
[*]/etc/FlexBuilder/bin/ is exported in ~/.bashrc, it seems SciTE doesn't "see" that?
[/LIST]
 
[*]I can get it to work by doing this: [FONT=Courier New]command.build.*.as=/etc/FlexBuilder/bin/mxmlc $(FileNameExt) [FONT=Arial]...but it doesn't solve the whole problem (see below)[/FONT][/FONT]
[/LIST]
 
[*][FONT=Courier New][FONT=Arial]I also need a specific environment variable set (FLEX_HOME). This is not set in SciTE.[/FONT][/FONT]
[LIST]
[*][FONT=Courier New][FONT=Arial]If I do env in a terminal, FLEX_HOME is set.[/FONT][/FONT]
[*][FONT=Courier New][FONT=Arial]If I do [/FONT][/FONT][FONT=Courier New]command.build.*.as=env[/FONT][FONT=Courier New][FONT=Arial] in SciTE (just temp to see env), FLEX_HOME is ***not*** set.[/FONT][/FONT]
[*][FONT=Courier New][FONT=Arial]FLEX_HOME is also set in ~/.bashrc[/FONT][/FONT]
[/LIST]
 
[/LIST]
So I guess SciTE is running a different shell profile... what I need to know is how to tweak things so that SciTE sees the same path and environment variables as my login shell. I assume it work would work fine then!

Oh, I tried "chown cam scite" so that I (and not root) own the scite exe, in the naive hope that this would somehow suck in my .bashrc, but apparently not =]

Any help appreciated. Overall I'm *loving* Ubuntu, so I hope I can get this issue cleared up (and maybe learn something new about linux in the process).

Cam.

---

### Post by invisisci on 2009-12-29
OK, got it to work with:

[FONT=Courier New]command.build.*.as=bash --login -exec '*command*'[FONT=Arial]

...in other words, instead of calling command directly, I invoke bash, tell it to be a login shell (which reads my .bashrc), then exec the command. Works perfectly.
[/FONT][/FONT]

---

