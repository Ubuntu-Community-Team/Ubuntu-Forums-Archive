---
title: "writing terminal files?"
date: 2011-09-07
forum: General Help
---

### Post by Xtensity on 2011-09-07
This is very basic i'm sure but I don't really know what to search to figure it out.

For instance, in windows I would make .bat files for running whatever in CMD.

How do I make similar files for the terminal in ubuntu?

---

### Post by haqking on 2011-09-07
> **Xtensity said:**
> This is very basic i'm sure but I don't really know what to search to figure it out.

For instance, in windows I would make .bat files for running whatever in CMD.

How do I make similar files for the terminal in ubuntu?

it is called **shell** scripting

[https://help.ubuntu.com/community/Beginners/BashScripting](https://help.ubuntu.com/community/Beginners/BashScripting)

see here also asked yesterday [http://ubuntuforums.org/showthread.php?t=1839796](http://ubuntuforums.org/showthread.php?t=1839796)

Edit: good point from WorMzy below ;-)

---

### Post by WorMzy on 2011-09-07
Technically, it's called *shell* scripting. Bash is just the most commonly used shell, but you can use any shell you want -- bash, dash, zsh, ksh, python, etc. just so long as you have the shell installed.

---

### Post by papibe on 2011-09-07
In Ubuntu (and most Linux systems) the CMD equivalent it is usually referred as terminal or command line. A terminal usually runs a shell or interpreter. In Ubuntu the default shell is called Bash.

As in Windows you can write .bats, you can write bash scripts (or just scripts).

[Here]("http://www.panix.com/~elflord/unix/bash-tute.html")'s a simple guide.

To get more tutorials google terms like:
[LIST]
[*]Introduccion to Bash.
[*]Bash tutorial.
[*]Bash basics.
[*]Bash scripts
[*]etc.
[/LIST]
Hope it helps,
Regards.

---

### Post by sisco311 on 2011-09-07
Unfortunately, most of the published shell/bash books are relatively poor, I don't even want to talk about the various guides available on-line.

So, please don't search the Net for random guides.

Trust me :) and check out the BashGuide from my signature. ;)

---

### Post by sisco311 on 2011-09-07
> **papibe said:**
> 
[Here]("http://www.panix.com/~elflord/unix/bash-tute.html")'s a simple guide.


Wow, this one is surprisingly accurate, short but at least accurate.

---

### Post by sujoy on 2011-09-07
tldp is your friend.

[Here's the bash section.]("http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html")

---

### Post by sisco311 on 2011-09-08
> **sujoy said:**
> tldp is your friend.

[Here's the bash section.]("http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html")

Last updated 11 years ago... RIP...

A horrible tutorial. A good place to hunt for BashPitfalls...

---

### Post by MG&amp;TL on 2011-09-08
I personally like LinuxCommand.org

Basic syntax is:

#!/bin/bash
<commands here>

Then give the file a .sh file extension, and run it via terminal by sh <your script>.sh

---

### Post by adelaide887 on 2011-09-08
> **MG&TL said:**
> I personally like LinuxCommand.org

Basic syntax is:

#!/bin/bash
<commands here>
[r4 card](http://www.thegerar.com/R4-Card-R4i-Card-R4-Cards-R4-i-Cards.html)
Then give the file a .sh file extension, and run it via terminal by sh <your script>.sh


yes i do so...;)

---

