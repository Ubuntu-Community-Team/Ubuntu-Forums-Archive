---
title: "Running binary files in terminal"
date: 2006-02-18
forum: General Help
---

### Post by Vilius on 2006-02-18
Hi,
I want to run some executable exec_name using terminal.

When I typed >exec_name I got:
bash: exec_name: command not found
( that file is in my curren path )

then I tried ./exec_name
it worked with no problems.

I know that ./ is used to avoid conflicts with apps in the $PATH.
But there are NO other exec_name files in my $PATH.

So why I can't just type >exec_name ?

sorry for my poor english
thanks

---

### Post by dcstar on 2006-02-18
[QUOTE=Vilius]Hi,
I want to run some executable exec_name using terminal.

When I typed >exec_name I got:
bash: exec_name: command not found
( that file is in my current path )

then I tried ./exec_name
it worked with no problems.

I know that ./ is used to avoid conflicts with apps in the $PATH.
But there are NO other exec_name files in my $PATH.

So why I can't just type >exec_name ?

sorry for my poor english
thanks[/QUOTE]
Linux does not default to running programs in the directory you happen to be in (unlike DOS).

You can set this up in your shell profile, but it is a security issue as you may want to run two different things with the same name, and depending on what directory you happen to be in, one or the other would be chosen.

Linux requires you to specifically choose an executable that is not in your paths, this is better than the ambiguity DOS allows.

---

### Post by Vogateer on 2006-02-18
I'm afraid I'm not too clear on waht you're asking for, but it sounds like everything is running the way it's supposed to.  Your $PATH should only include directories, and when you type in the name of a program, it searches only in those directories listed in your $PATH.  You can add "./" into your PATH so that it automatically searches for whatever folder you're in, but that's considered bad security.  It's better to put your executables in "~/bin" or "/usr/local/bin" and make sure whichever directory you use is listed in your $PATH if you plan on accessing them often.  You should be able to add directories to your path thus:

export PATH=$PATH:/usr/local/bin:$HOME/bin

If you want to ignore the security precautions, and execute in the local directory without "./", do this:

export PATH=$PATH:./

At least, I think that will work.

But using "./" before the "exec_name" just forces bash to use the current directory for the executable, and is really no different than if you had typed out the entire absolute path.

---

### Post by taurus on 2006-02-18
[QUOTE=Vogateer]I'm afraid I'm not too clear on waht you're asking for, but it sounds like everything is running the way it's supposed to.  Your $PATH should only include directories, and when you type in the name of a program, it searches only in those directories listed in your $PATH.  You can add "./" into your PATH so that it automatically searches for whatever folder you're in, but that's considered bad security.  It's better to put your executables in "~/bin" or "/usr/local/bin" and make sure whichever directory you use is listed in your $PATH if you plan on accessing them often.  You should be able to add directories to your path thus:

export PATH=$PATH:/usr/local/bin:$HOME/bin

If you want to ignore the security precautions, and execute in the local directory without "./", do this:

export PATH=$PATH:./

At least, I think that will work.

But using "./" before the "exec_name" just forces bash to use the current directory for the executable, and is really no different than if you had typed out the entire absolute path.[/QUOTE]
Actually, it's just

PATH=$PATH:.
export PATH

---

