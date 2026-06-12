---
title: "nvidia display settings"
date: 2009-12-06
forum: General Help
---

### Post by karmicgaz on 2009-12-06
Ok,I've posted elsewhere on the forum with this issue but here goes again. After altering my display resolution it will not save. Will not parse with xorg.conf. There is no xorg.conf.
Have had some help previously to no avail, I know a little more now. Have attached screenshot. Also periodically the screen flickers/refreshes which it didn't do before (could be monitor is about to die) but just thought I'd mention it.

---

### Post by D3SI on 2009-12-06
same problem here.. just tried and i get same error.

---

### Post by karmicgaz on 2009-12-06
I posted this yesterday or day before and got lots of help, one I will attach here to see if it works for you. Let me know.

Nvidia Proprietary Drivers need nvidia-settings to set screen resolution and change other settings. In previous versions of Ubuntu and in other distros to make them permanent (used in every session) you click the “Save to X configuration file”. From Karmic on there is no xorg.conf by default!

As a result, nvidia-settings is not able to save the settings and every time I logged in I had  to change the resolution (Phew!!!). Then Sathya helped me. He gave me a  link from Ubuntu Forums. Then I did the following to fix the problem:

1. Press Crtl+Alt+F1 to go to tty1. (Crtl+Alt+F2 takes you to tty2 and so on. available till tty6).

2. You’ll be taken to a terminal. Press Crtl+Alt+F7 to return to the GUI screen. Now you need to kill Xserver from there. Type ‘/etc/init.d/gdm stop’ (use kdm in KDE).

3. If you are reading this and simultaneously following, you’ll lose this screen in this step. Now, type

    sudo Xorg -configure

4. This gives an xorg.conf in your home directory. It would be named “xorg.conf.new”.

5. Take this file to “/etc/X11&#8243; and rename it ‘xorg.conf’.

6. Now click “Save to X configuration file” in nvidia-settings. Note that you need root permissions to do this.

7. Now your settings will be saved. Make a copy of that file back in your home directory, if needed, and rename it to “xorg.conf.new” (replacing the original).

8. You’re Done. Try logging off and back in.

---

### Post by karmicgaz on 2009-12-06
I have tried doing this but it tells me not to use /etc/init.d/ but instead use service gdm stop                      Which doesn't work!                      WTF!

---

### Post by karmicgaz on 2009-12-06
So if I cannot stop gdm, I cannot create/move xorg.conf!

---

### Post by karmicgaz on 2009-12-06
Is your screen flickering d3si?

---

### Post by NoaHall on 2009-12-06
Try this -```
sudo nvidia-xconfig
``` then run```
gksudo nvidia-settings
```
You can just run these from a normal terminal, no need for ctrl + alt + F1

---

### Post by karmicgaz on 2009-12-06
That's brilliant! It worked!  Thankyou. I'm obviously a noob but I want to learn, I understand the sudo bit (in the root?) but what is gksudo?

---

### Post by NoaHall on 2009-12-06
gksudo is the command for running graphical applications :) You could use sudo, but gksudo is the correct way, because they work in different ways(in regards to themes etc).

---

### Post by karmicgaz on 2009-12-06
many thanks. I hope you get this d3si. It worked for me.

---

### Post by karmicgaz on 2009-12-06
Mind you my screen still flicking, probably knackered!

---

### Post by NoaHall on 2009-12-06
> **karmicgaz said:**
> Mind you my screen still flicking, probably knackered!

That's quite strange. Are you using the latest driver and do you have compiz enabled?

---

### Post by karmicgaz on 2009-12-06
latest driver yes, whats compiz?

---

### Post by karmicgaz on 2009-12-06
yes compiz installed

---

### Post by NoaHall on 2009-12-06
Try disabling compiz(by turning off the visual effects through System -> Preferences -> Appearance)

---

### Post by karmicgaz on 2009-12-06
They were turned off, now turned them on. (middle option as onboard graphics) but still flickering!

---

### Post by karmicgaz on 2009-12-06
Probably the monitor, it's quite old.

---

### Post by karmicgaz on 2009-12-06
Sorry, I should clarify, monitor seems fine for up to 3mins at a time then flashes, like doing a restart, sometimes only a few seconds apart, but always returns, as I said probably the monitor is about to die!
Will ubuntu have problems with me just plugging a new one in?

---

### Post by NoaHall on 2009-12-06
Nah, just get a new one, it'll be fine.

---

