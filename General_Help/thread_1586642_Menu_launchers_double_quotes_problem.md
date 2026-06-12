---
title: "Menu launchers double quotes problem"
date: 2010-10-02
forum: General Help
---

### Post by _sluimers_ on 2010-10-02
Using Mint 9 xfce and mint's gnome menu (thus gnome terminal).

I'm trying to make some menu button that would start examples of the rpgmaker I co-develop. I have made the engine so, that 
ika /path/to/the\ game would start the game. 
Of course it can be done between double quotes like this:
ika "/path/to/the game"
but menu launchers won't take that and start giving me child errors.

My question is, am I forced to use extra backslash characters for this?

---

### Post by gzarkadas on 2010-10-02
If you pass a string with spaces to the shell unquoted, you have to use backslashes, else the shell will think that it is more than one string (space is a string delimiter). 

Your question however, indicates to me that you do not merely want to launch an app only. Does your ika engine uses the path to read or execute further files located at that path? 

If yes, either of quotes/backslashes in the menu launcher (I suppose a .desktop entry) should succeed for your app to get the entire string as one argument. Your app however should then arrange to provide it to the shell either quoted or with backslashes embedded.

If your app cannot - or you do not want - to do this and it only uses the string to read/execute other files _one level deep_, then you can just pass a string of `path/to/the\\\ game' or `"path/to/the\ game"' to it; that is you prepare the string such that it is properly backslashed for the 2nd shell (the first will remove quotes/eat a backslash upon calling your ika executable).

But if your child processes will then call other child processes, then the above is not enough and so you would have to make a routine that either quotes or backslashes the input appropriately.

---

### Post by _sluimers_ on 2010-10-03
ika searches for a file called game.ika-game file located at that directory.

And yes, it's a .desktop entry. I notice that if they're not working when I install them in /usr/share/applications, despite adding them manually.   :/ 

The thing is, my app works fine with or without quotes, but the menu launcher seems to have problems with both in different ways.
I can't even edit them.

```

Could not save launcher
Failed to create file '/usr/share/applications/ika-map-example.desktop.ZM73JV': Permission denied

```

Without quotes they open a terminal and close immediately, despite when adding a menu button manually

With quotes... hey I've been trying it again.. same problem now, it opens the terminal and quits, despite that a manually created menu button would start the game.

So the quotes are now no longer a problem.
I should probably mark this solved, despite running into other problems, hmm....

---

### Post by gzarkadas on 2010-10-03
/usr/share/applications is owned by root. You must `sudo' to root in order to be able to _write_ there. When you create a desktop entry (a launcher) in your desktop this is a directory owned by your account. I believe the problem demonstrated in your previous post is that kind of problem.

---

### Post by _sluimers_ on 2010-10-03
When my package copies the desktop files to /usr/share/applications, they show up as owned by root with the same permissions as the other desktop files when I type ls -l on them.

---

### Post by gzarkadas on 2010-10-04
Then it is not file permissions problem, but without a case (such as a piece of code that fails) it is hard to say anything else. One last piece to look is the possibility that the menu launcher is ok, but the script/application that calls aborts with an error during its initial steps, so the terminal closes before having the opportunity to see it.

---

### Post by _sluimers_ on 2010-10-04
I did that. Here's the problem I'm having now:

ika /usr/share/ika/ika-examples/Hello world or
ika "/usr/share/ika/ika-examples/Hello world"
```

Game Startup: /usr/share/ika/ika-examples/Hello/game.ika-game does not exist.

```

ika /usr/share/ika/ika-examples/Hello\ world or
ika "/usr/share/ika/ika-examples/Hello\ world"
```

Game Startup: /usr/share/ika/ika-examples/Hello\\/game.ika-game does not exist.

```

---

### Post by gzarkadas on 2010-10-04
I read the code in your svn; it looks right. So the problem seems to be that the argument string is not passed to your argv[] array as one argument. However it would not hurt to issue a debug statement in your main to see what you actually get.

Since you do not add backslashes in your code, you must supply all in the launcher call. That is you must put an escaped backslash and an escaped space (that is '\\\ ' in the unquoted example). Also it is better to use single quotes instead of double ones; it makes handling of backslashes a bit more easy. You can also try the $'...' form (last line) to pass the space as an octal C char-sequence.

So, first check these (my best guess):

```

ika /usr/share/ika/ika-examples/Hello\\\ world
ika '/usr/share/ika/ika-examples/Hello\ world'
ika $'/usr/share/ika/ika-examples/Hello\\\040world'

```If they do not work, fiirst sub a backslash and try (ie try with n-1), then add one to the above exaples and try again (n + 1).

A workaround would be to *not* use backslashes / quotes and instead concatenate all arguments using " " as join element (or "\\ " if a backslash is required by the open function). It is a workaround and not a real solution because it forbids you in the future to add other arguments to your main executable.

---

