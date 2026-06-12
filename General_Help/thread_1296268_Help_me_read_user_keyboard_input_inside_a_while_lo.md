---
title: "Help me read user keyboard input inside a while loop in a bash script"
date: 2009-10-20
forum: General Help
---

### Post by Brionius on 2009-10-20
Hi folks,
     Thanks in advance for reading this!  I'm having trouble getting user input in a bash script.  Normally I have no problems using the bash "read" builtin.  But for some reason, when I try to get user input inside a while loop, the "read" function REFUSES to stop and wait for user input!  Here's the offending code snippet:

```
  
execute=3
while [ $execute -eq 3 ]
do
     read -p 'Type "yes" to execute, "skip" to skip for this file, or "exit" to stop.' confirm
     case $confirm in
          "yes") execute=1 ;;
          "skip") execute=0 ;;
          "exit") exit 0 ;;
          * ) execute=3
          echo 'Please enter a valid option.'
          ;;
     esac
done

```This is part of a larger script, but the rest of it worked fine until I added this (the "interactive" mode for my script).  The result running this is an infinite stream of "Please enter a valid option." without any pause for input.

Can anyone tell me what I'm doing wrong?  Why won't "read" wait for input inside this while loop?  Thanks!

---

