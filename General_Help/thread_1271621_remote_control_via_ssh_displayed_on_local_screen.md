---
title: "remote control via ssh displayed on local screen?"
date: 2009-09-21
forum: General Help
---

### Post by makkan77 on 2009-09-21
I've made a digital picture frame (DPF), you can check it out [here]("http://genericnerd.blogspot.com/2009/05/converting-toshiba-320cds-to-digital.html"). To control it remotely I use x11vnc and sshd. However I would like to skip X and just have the console displayed in the frame. The problem is that I don't know how to display what I do remotely via ssh on the DPF-screen. 

An example of what I want to achive: When I boot the DPF it automatically logs in and starts whatever application I want running. If I want to change something I log into my DPF via ssh. While I do this everything I write and do is also displayed on the DPF-screen. 

I thought this would be quite easy to solve with GNU screen but so far I haven't found what I'm looking for yet.

---

### Post by makkan77 on 2009-09-21
well I found it, 
apparently screen -x does exactly what I needed...

well no that didn't work. I want screen to follow me when I change window aswell.

---

