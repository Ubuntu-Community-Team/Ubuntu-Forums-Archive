---
title: "Good place to start learning the bash shell better?"
date: 2010-11-22
forum: General Help
---

### Post by ninjaaron on 2010-11-22
Little story first. If you don't care, the real question is at the bottom.

So, I've been using Ubuntu for about three years now, and I was using OSX for some five years before that. So after eight years in the Unix-based world, I figure I should learn some things. So far, I just know a few commands: cd, rm, mv, cp, ls, find; a few modifiers for each; and I know how to run a couple of basic apps through the terminal like apt-get, alsa, nano and of course man. I've had to use 'make' and 'build' a couple of times, but I never knew what I was doing, and it was a nightmare each time. I'm not totally sure I've ever succeeded at building from a binary, come to think of it.

So recently, I needed to change four-thousand file names from upper to lower case for whatever reason. I figured there must be a better way to do this than renaming each one of them in a GUI's file browser. There was. I found a simple ten-line script and figured out how to make it a shell command. After that, I even found a single line command that did the same thing; ```
for i in `find * -depth`; do (mv $i `echo $i|tr [:upper:] [:lower:]`); done
```

After looking at this command for a minute or two (and looking at the man page for tr), I realized that all of the commands in these lines made sense to me. That's when I decided I probably have the ability to figure out how to use this 'bash' thing properly.

**So the real question is,** where should I begin learning about the shell and scripting? reading man pages doesn't really seem like the way to do it. I worked with Basic for two years in high school, C++ for one year (though this was seven years back), and I've done a bit with markup languages as well (HTML, XML, CSS), so I kinda 'get' this stuff. Just don't know where to start with the shell.

---

### Post by sohlinux on 2010-11-22
I have learned everything I know by just googling , reading forums watching youtube videos etc then making notes in notepad. if you want to be a guru you could do a course there are plenty online.

---

### Post by Portmanteaufu on 2010-11-22
Isn't it so satisfying when you manage to get it done in one command? :D

I'd like to mention that there is a valuable distinction to be made between 'Learning Bash' and 'Learning common Unix utilities.'

Bash itself is the thing reading your commands and executing them. However, most of your commands are going to be comprised of programs that are independent from Bash. For example, 'tr' from your example above is a standalone program. You could use it from any shell, not just Bash. The portion of your example code that's specific to Bash would be the syntax of the for loop you used.

This distinction is often glossed over by tutorials and command lists [like this one]("http://ss64.com/bash/"), but will probably help you when you're looking for more information. Knowing when to fight the temptation to include "bash" in your Google searches can really help to weed out the irrelevant results.

---

### Post by Slim Odds on 2010-11-22
I agree very much with [Portmanteaufu]("http://ubuntuforums.org/member.php?u=631265")

There is also a some very good information in the Advanced Bash Scripting guide.

[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

Just remember, like Portmanteaufu says, many of the command that you use in shell scripts are external commands. One of the great beauties of Unix/Linux is that you can mix and match tons of small tools to get a new job done.

---

### Post by Grenage on 2010-11-22
You can read guides until you're blue in the face, but (short of a photographic memory) you'll not remember what you don't utilise.

If you don't have a problem to solve, invent one - then look for a solution.

---

