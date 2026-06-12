---
title: "Ardour/Jack setup help?"
date: 2011-08-22
forum: General Help
---

### Post by dizzygamr on 2011-08-22
:confused: I am terribly lost. Seeing as I am a newbie to all of this installing I suppose it was imminent.My problem is I'm trying to record audio via the microphone input on my computer tower into a music production software (in this case ardour), and I can't get the software to start.

What I did: I went to synaptic package manager and downloaded "ubuntustudio - desktop" which in turn downloaded some other files to get it all running. I then proceeded to to the SPM and download "ardour" and it's related files. 

The issue: I need to get a music program up and running, and a good one (ardour), audacity doesn't cut it, please don't suggest it. When I simply try to start ardour by going to "applications -> sound&video -> audio production -> ardour GTK2" it gives me a window to set parameters, which i know nothing about, then when i simply press start, it gives me an error which reads:

"1) You requested audio parameters that are not supported..
2) JACK is running as another user."

Just to reiterate, my issue is not connecting wires or getting the audio from the physical world in, it is getting ardour and this "JACK" program to cooperate. Simply put "How do I get Ardour to cooperate with JACK (both installed already) So that I may use ardour for my music?"

---

### Post by luctor on 2011-08-22
try starting Jack via qjackctl , a nice gui for jack. see if that helps.

---

### Post by luctor on 2011-08-22
and this topic should be moved to the Ubuntu Studio section! :-)

---

### Post by dizzygamr on 2011-08-22
OK, so i went and tried to start "JACK Control", and it came up with an error message saying:

"Could not connect to JACK server as client.
- Overall operation failed.
- Unable to connect to server.
Please check the messages window for more info."

And the message window it was referring to read:

"18:58:24.870 JACK was stopped with exit status=255.
18:58:24.871 Post-shutdown script...
18:58:24.872 killall jackd
18:58:25.054 ALSA connection change.
jackd: no process found
18:58:25.283 Post-shutdown script terminated with exit status=256."

As the last few commands (following a copyright statement).

So after some tinkering I found the "connections" tab in the little JACK box, and in that window i went to the "ALSA" tab, seeing as that was one of the options in the Ardour setup box (mentioned earlier). In that tab i found Ardour in the right and left boxes, so I clicked on both and hit connect. This then drew a line between the two, so i tried to start up ardour. Same message came up. Am I missing something?


P.S.
Huge newbie here, how exactly do I move this to a different forum topic?

---

### Post by dizzygamr on 2011-08-22
ATTENTION: just figured out my problem. After hours of forum and support-site searching I've found that my issue was simple, simple enough to make me laugh hysterically.

The issue's solution: Upon opening JACK control again it gave me the same error, fine, BUT i went into settings and compared with a youtube video I was (i suppose currently am) watching and on the far left there's a bunch of checkboxes. I had "realtime" checked, so i unchecked it and saved the settings. Runs fine now. Thought i'd post this for anyone who should come across the same issue.

---

