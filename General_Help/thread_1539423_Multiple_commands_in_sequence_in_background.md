---
title: "Multiple commands in sequence in background"
date: 2010-07-26
forum: General Help
---

### Post by J V on 2010-07-26
I like background commands in scripts:
```
sudo apt-get update&
```
I also like multiple commands in scripts:
```
sudo apt-get update && sudo apt-get upgrade
```
How would I combine these? Could I do it with functions?

---

### Post by bodhi.zazen on 2010-07-26
Combine what ?

Write a script

```
#!/bin/bash

# Comments on what the script does
# More comments

command1 &
command2 &

apt-get update && apt-get upgrade -y &
```

Is there some script you are having a problem with ?

You may also like screen.

---

### Post by J V on 2010-07-26
Say I wanted something like this (Very pseudo code) so that both commands would run in the background but would use the && operator so that the later ones would only work if the first one exited correctly.
```
sudo apt-get update & && sudo apt-get upgrade &
```

Could I also do this?
```
function lol {
sudo apt-get update && sudo apt-get upgrade
}
lol &
```

---

### Post by ajgreeny on 2010-07-26
A far as I'm aware you must either use one ampersand or two, but you can not use one then follow it with two as you did in the  ```
sudo apt-get update & && sudo apt-get upgrade &
``` because the single one & means run the two commands one after the other, but not waiting for the first to finish, while the two & means run the second command after the first has concluded successfully.

So as far as I can see you simply need the two & to do what you are trying to do.  You may need to run the script in gnome terminal, however, if you wish to see any error messages should the script not run either part successfully.

---

### Post by bodhi.zazen on 2010-07-26
> **J V said:**
> Say I wanted something like this (Very pseudo code) so that both commands would run in the background but would use the && operator so that the later ones would only work if the first one exited correctly.
```
sudo apt-get update & && sudo apt-get upgrade &
```Could I also do this?
```
function lol {
sudo apt-get update && sudo apt-get upgrade
}
lol &
```

You may run the update in the BG, but the upgrade would then fail as apt is already running.

for those two commands, you need to wait for the update to finish, thus use the &&

For the upgrade, add the -y flag or it will hang asking if you wish to proceed with the upgrade.

---

### Post by J V on 2010-07-27
Good point about the y flag, so I assume I can just make it like this:
```
sudo apt-get update && sudo apt-get -y upgrade &
```and the whole line will run in the background? I have other elements of the script I want to run.

---

### Post by CharlesA on 2010-07-27
That would run apt-get update in the forground, and apt-get upgrade in the background.

I suppose you could try making a seperate script for the upgrade or just do this to hide the output:

```
sudo apt-get update > /dev/null && sudo apt-get --assume-yes upgrade > /dev/null
```

Only problem with that is that if there are errors, you won't know about them and you won't get a shell prompt back until both commands are done.

---

### Post by J V on 2010-07-27
If I put them in a function and ran the function in the background:```
function test {
sudo apt-get update && sudo apt-get upgrade
}
test &
```would that work?

---

### Post by CharlesA on 2010-07-27
Might work, you can give it a shot. :)

---

### Post by J V on 2010-07-27
It worked!

```
#!/bin/bash

function t {
echo "lol" && sleep 5 && echo "lol"
}

t &
```

But I would still need a method to keep track of processes so that I can hold off certain commands from being executed until the last one is done...

I can close this now, moved main questions onto another thread.

---

