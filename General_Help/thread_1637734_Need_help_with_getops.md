---
title: "Need help with getops"
date: 2010-12-04
forum: General Help
---

### Post by BlackMoor on 2010-12-04
Greetings,

I need some help with using getops in the bash shell.  I want to be able to use multiple options at the same time and some of those options will require an argument and some will not.

Here is my bash script:

[B]#!/bin/bash

while getopts ":a:bc:de:fg:" opt ; do
  case $opt in
    a)
      echo "-a was triggered, [/B]**Argument**[B]: $OPTARG" >&2
      ;;
    b)
      echo "-b was triggered" >&2
      ;;
    c)
      echo "-c was triggered, Parameter: $OPTARG" >&2
      ;;
    d)
      echo "-d was triggered" >&2
      ;;
    e)
      echo "-e was triggered, [/B]**Argument**[B]: $OPTARG" >&2
      ;;
    f)
      echo "-w was triggered" >&2
      ;;
    g)
      echo "-g was triggered, Argument: $OPTARG" >&2
      ;;

    \?)
      echo "-$OPTARG is not a valid option" >&2
      exit 1
      ;;
    
      echo "-$OPTARG must have an argument." >&2
      exit 1
      ;;
  esac
done[/B]

This is my problem:

[B]BlackMoor@home~>./beta.bash -a -b
-a was triggered, [/B]**Argument**[B]: -b
[/B]
I ran my script with two options. The first option -a, requires an argument.  However, instead of giving me an error reporting that option -a requires an argument it takes option -b as the argument though that is an option....

[B]BlackMoor@home~> ./beta.bash -z -b
Invalid option: -z

BlackMoor@home~> ./beta.bash -a -z
-a was triggered, Argument: -z

BlackMoor@home~> ./beta.bash -a
-a [/B]**must have an argument.**

If I only use option -a with no arguments, the script works...

If someone can help me fix this problem that would be much appreciated.

---

### Post by Brandon Williams on 2010-12-06
I believe that this is simply the way that getopts works. It would not be able to reliably determine that "-b" is not a perfectly valid argument for "-a", so it assumes that it is. To the best of my knowledge, this is true of the alternatives, too.

---

