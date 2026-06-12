---
title: "How to launch multiple programs via script?"
date: 2010-04-25
forum: General Help
---

### Post by root.talis on 2010-04-25
Hi.

I need to make a (bash, pearl) script to launch a number of programs paralelly. Actualy, I need to:

```

Launch jackd -d asla
Wait for it to start up (say, sleep 3)
Launch fluidsynth -l -r 48000 ~/synth/synthname.sf2
Wait for it to start up (say, sleep 2)
Launch jack_connect system:playback_1 fluidsynth:left
Launch jack_connect system:playback_2 fluidsynth:right
Launch aconnect 20:0 128:0

```What I want to do is to automatically start up a MIDI-playing system in one terminal. Usually to handle all of this I need to open a tab for jackd, a tab for fluidsynth and a tab for connections. I want to automate this.

I've tried this code:
```

jackd -d alsa &
sleep 4
fluidsynth -l -r 48000 ~/synth/somefont.sf2 &
sleep 3
jack_lsp
sleep 2
jack_connect system:playback_1 fluidsynth:left
jack_connect system:playback_2 fluidsynth:right
aconnect 20:0 128:0
echo Done
```It starts up jackd, waits, starts up fluidsynth (and i get a command prompt), then when it gets to jack_lsp it shows no ports for "fluidsynth". When I try to killall fluidsynth it says that there is no any fluidsynth launched. Seems like fluidsynth shuts down when I try to run it in bg (even if there are no other processes in bg). Am I doing something wrong?

I would really appreciate any help. Thank you.

---

### Post by Brandon Williams on 2010-04-27
I'm not familiar with fluidsynth. Are you certain that it will run correctly in the background with command line you've specified? Is there some sort of user interface (maybe just reading lines from the terminal) on the application? And if so, is there a command line switch that you can use to tell it that you don't want the user interface?

---

### Post by root.talis on 2010-04-29
Thank you for your reply.

I see your point. Yes, there is a command line. I've launched fluidsynth --help and here is what I've found:

```
-i, --no-shell
    Don't read commands from the shell [default = yes]
[...]
s, --server
    Start FluidSynth as a server process
```These two switches do the job:

```
fluidsynth -l -r 48000 /home/user/synth/somesynth.sf2 -i -s &
```Thank you.

---

