---
title: "trap ctrl-c (SIGINT) inside bashrc function"
date: 2011-01-12
forum: General Help
---

### Post by wltj on 2011-01-12
Hi, I'm trying to catch ctrl-c keypress inside a bashrc function called 'sripmp'. The trap function (nested in sripmp) is called 'controlc'. In the command (in the else clause at bottom), you can see I have to fork streamripper to the background using &, then sleep for a few seconds while streamripper creates a buffer, and then listen to SR's relay with mplayer. So I want the trap to catch ctrl-c, then kill the streamripper background process before exiting the function altogether. Here is the function: 

```
sripmp() {

RIPDIR=/mnt/audio/streamrips

# function to run on control-c keypress
controlc() {
    echo "Caught Ctrl-C SIGINT. Cleaning up..."
    pkill streamripper
    exit $?
}

if [ "$#" -ne 1 ]; then
    echo "usage: sripmp http://streamurl"
else
    trap controlc SIGINT
    streamripper $1 -r -q -i -d "$RIPDIR" -u Mozilla/5.0 --quiet & sleep 5 && mplayer http://127.0.0.1:8000 -really-quiet
fi
}
```

I've tried putting the 'trap controlc SIGINT' at the top of the function and within the else clause before the streamripper command, where it is here. Ive also tried 'trap controlc 2'. But controlc is never executed. Any help is appreciated!

---

