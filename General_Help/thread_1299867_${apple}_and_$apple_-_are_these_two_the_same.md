---
title: "${apple} and $apple - are these two the same?"
date: 2009-10-24
forum: General Help
---

### Post by dandeliondream on 2009-10-24
Hi,

Are ${apple} and $apple the same?

---

### Post by AlphaLexman on 2009-10-24
> **dandeliondream said:**
> Hi,

Are ${apple} and $apple the same?

What are you doing? Are you in a .conkyrc file or what? In conky they would be the same, but '${apple 12}' is not the same as '$apple 12'

---

### Post by dandeliondream on 2009-10-24
> **AlphaLexman said:**
> What are you doing? Are you in a .conkyrc file or what? In conky they would be the same, but '${apple 12}' is not the same as '$apple 12'

I'm working on a bash shell script. I am unsure if i should use ${apple} or just $apple. I think they are the same. Please correct me if i'm wrong :confused:

---

### Post by geirha on 2009-10-24
They are the same yes. You usually don't need the {} but they are sometimes required.

```
foo="Hello, "
echo "$fooWorld"
echo "${foo}World"
echo "$foo"

```
With the first echo-command, it will replace $fooWorld with the contents of the variable fooWorld, but fooWorld has not been set (only foo), so the output will be nothing (just a new line).

In the second case, foo is enclosed in {}, so it will replace ${foo} with the contents of the variable foo, and the echo will output "Hello, World".

In the last case, there's no room for ambiguation. "$foo" will be replaced with "Hello, ".

See [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide) for more information.

---

### Post by dandeliondream on 2009-10-24
> **geirha said:**
> They are the same yes. You usually don't need the {} but they are sometimes required.

```
foo="Hello, "
echo "$fooWorld"
echo "${foo}World"
echo "$foo"

```With the first echo-command, it will replace $fooWorld with the contents of the variable fooWorld, but fooWorld has not been set (only foo), so the output will be nothing (just a new line).

In the second case, foo is enclosed in {}, so it will replace ${foo} with the contents of the variable foo, and the echo will output "Hello, World".

In the last case, there's no room for ambiguation. "$foo" will be replaced with "Hello, ".

See [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide) for more information.

thank you for the explanation :KS

---

