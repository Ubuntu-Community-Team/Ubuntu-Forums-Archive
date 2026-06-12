---
title: "Can't get Terminator to show cowsay and cd at startup"
date: 2012-07-26
forum: General Help
---

### Post by vaviary on 2012-07-26
**Sorry in advance if I'm either in the wrong category or not always posting the correct menu points, I'm running Ubuntu in German.**

I'm running Ubuntu 12.04 with Gnome Shell.
Today I installed Terminator and I like it very much. This is a screenshot of my default layout: [http://ubuntuone.com/1KHrMvvwRJ3MTTwhqOezQX](http://ubuntuone.com/1KHrMvvwRJ3MTTwhqOezQX)
 
So, I thought it'd be cool to run…

[LIST]
[*]"fortune|cowsay -f tux" in the upper right…
[*]"cd ~/py" in the bottom right…
[/LIST]
…terminal at startup, but then get the normal Bash prompt.

But I immediately failed at the first try.
I found right click -> Settings -> Layouts -> "custom command" input box,
but putting "fortune|cowsay -f tux" or "cd ~/py" just crashes that terminal at startup.
Same with

[LIST]
[*]"/bin/bash fortune|cowsay -f tux"
[*]"bash -c fortune|cowsay -f tux"
[*]"gnome-terminal -e 'fortune|cowsay -f tux'" (Here it spawns a new window with the cow in it, but then it disappears.)
[/LIST]
_[Here]("http://lmpeiris.wordpress.com/2011/01/17/cowsayhow-to-make-a-cow-talk-on-terminal-startup/")_ it says to put it in the .bashrc file, but I didn't try that, because wouldn't it then run in all three terminals?

So this is pretty much the problem. I would be very happy If someone could help me.

P. S.: There's also that annoying message every time i want to close Terminator:
"Close multiple terminals?", I'd appreciate it much if someone could tell me how to deactivate that.

Thanks in advance!

---

