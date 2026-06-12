---
title: "Screen sharing into 10.04LTS securely, internationally."
date: 2011-05-07
forum: General Help
---

### Post by DrCR on 2011-05-07
I got a friend who's about to head out to some foreign part. I would like to be able to help support his more technical needs (he does a pretty remarkable job on his own for most stuff) by being able to remote into his computer i.e. screen sharing so I can walk him through whatever it is that he needs assistance in.

He is running 10.04LTS. 


The only remoting in I'm used to is an occasinal ssh command line session to a local NAS. And the little GUI remoting in I done (which is what we want in this case) has been VNC in windows and MS's remote desktop, both on internal networks, so I'm calling for some input from you guys.


The traffic definitely needs to be encrypted, and I would like to be able to set up his machine such that he security is not compromised. 



Thoughts? I would greatly appreciate input. I'll be reading up here and abroad in the mean time.

Thanks

---

### Post by mikewhatever on 2011-05-07
[TeamViewer (wine application)]("http://www.teamviewer.com/")
[NoMachineNX]("http://www.nomachine.com/")
'ssh -X' lets you launch graphical apps via ssh
'ssh -L 5900:localhost:5900' - VNC via ssh 

Either of the above should do. It's probably best to test the chosen solution while your friend is still around.

---

