---
title: "No sound over ssh -x"
date: 2010-01-17
forum: General Help
---

### Post by zeezam on 2010-01-17
Before I have played spotify, youtube etc over ssh -x to my htpc but after some updates (i guess) it has stopped working :(
In spotify I get "problem with your sound card". If I play something in the web browser I get no sound. I have tried /etc/init.d/alsa-utils restart and reboot on the target computer.

---

### Post by juhani on 2010-01-27
I confirm this one. I'm trying to SSH to my computer which is connected to my stereo system to control music playing from a different computer. Problem seems to be with ALSA, and it has appeared on each music player I've tried, including Spotify, Amarok1.4 and mocp. When I log on to my computer locally, sound works perfectly out of the box.

mocp output over ssh:
```
$ mocp
Running the server...
Trying JACK...
Trying ALSA...
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2211:(snd_pcm_open_noupdate) Unknown PCM default
Trying OSS...

FATAL_ERROR: No valid sound driver


FATAL_ERROR: Server exited

```


```
$ lspci | grep -i audio
00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)

```

Edit: don't know if this is of any use, but I logged in, started screen and attached to that screen over ssh and moc plays music ok this way if keep logged in through tty. If i log out from console, sound card disappears even from locally opened screen. I also tried things a bit further, and it would appear I can use at least spotify remotely over SSH with X forwarding and sounds work if I'm just logged in locally. Text-based login is enough, there's no need to log in using kdm.

---

### Post by juhani on 2010-02-23
Bump, and..

I happened to note that the exact same username has to be logged in locally for sound to work over ssh. At the moment there's a different username logged in to my computer in I'm logged in over ssh, and i don't have sound card available.

Obvious it seems, sound is somehow attached to logging in locally.

---

### Post by agarciamog on 2010-11-06
Bump...

Anyone figured out how to sound on moc over ssh,yet?

---

### Post by JasonFWard on 2011-12-06
Anyone with a solution to this?

Anyone at all?

---

### Post by killermist on 2011-12-07
Does the sound tunneling follow with X tunneling?
```
ssh -x
``` (lower case x) disables X tunneling, while ```
ssh -X
``` (upper case X) explicitly tries to establish X tunneling.

[edit]
[QUOTE="man ssh"]```
     -X      Enables X11 forwarding.  This can also be specified on a per-
             host basis in a configuration file.

             X11 forwarding should be enabled with caution.  Users with the
             ability to bypass file permissions on the remote host (for the
             user's X authorization database) can access the local X11 dis&#8208;
             play through the forwarded connection.  An attacker may then be
             able to perform activities such as keystroke monitoring.

             For this reason, X11 forwarding is subjected to X11 SECURITY
             extension restrictions by default.  Please refer to the ssh -Y
             option and the ForwardX11Trusted directive in ssh_config(5) for
             more information.

     -x      Disables X11 forwarding.
```[/QUOTE]

---

### Post by Dwaalspoor98 on 2012-11-19
Killing Pulseaudio on the client seems to fix this issue, there should be a more clean solution but didn't take the time to find one and this works.

So on the client:
pulseaudio -k

After that SSH to the machine which runs spotify:
ssh -XYC <node> spotify

---

### Post by wildmanne39 on 2012-11-19
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

