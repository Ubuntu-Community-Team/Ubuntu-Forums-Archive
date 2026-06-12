---
title: "How can I disable sound from Firefox only?"
date: 2010-05-02
forum: General Help
---

### Post by AaylaSecura on 2010-05-02
Hi! I was wondering if there's any way to block sound coming from Firefox. My problem occurs when I want to play some flash game that doesn't have an option to turn off the sound and I want to listen to music at the same time.

---

### Post by Jordanwb on 2010-05-02
If you open up gnome's sound control and go to the Applications tab, you can mute programs that are using sound.

---

### Post by AaylaSecura on 2010-05-02
I'm either blind or there's no application tab in my Sound preferences. To be clear - we're talking about System > Preferences > Sound, right. I only have Devices and Sounds tabs there.

---

### Post by dino99 on 2010-05-02
some kind of sound tunneling

[http://www.tutcity.com/tutorial/control-sound-volume-with-actionscript.12619.html](http://www.tutcity.com/tutorial/control-sound-volume-with-actionscript.12619.html)

---

### Post by Jordanwb on 2010-05-02
> **AaylaSecura said:**
> I'm either blind or there's no application tab in my Sound preferences. To be clear - we're talking about System > Preferences > Sound, right. I only have Devices and Sounds tabs there.

That's right. There should be five tabs: "Sound FX", "Hardware", "Input", "Output" and "Applications".

Picture: [http://img265.imageshack.us/img265/3240/screenshot3wb.png](http://img265.imageshack.us/img265/3240/screenshot3wb.png)

---

### Post by AaylaSecura on 2010-05-02
> **Jordanwb said:**
> That's right. There should be five tabs: "Sound FX", "Hardware", "Input", "Output" and "Applications".

Picture: [http://img265.imageshack.us/img265/3240/screenshot3wb.png](http://img265.imageshack.us/img265/3240/screenshot3wb.png)
Mine's a little bit different:

[http://i41.tinypic.com/5p4z0j.png](http://i41.tinypic.com/5p4z0j.png)
[http://i44.tinypic.com/2yyuvf6.png](http://i44.tinypic.com/2yyuvf6.png)

---

### Post by AaylaSecura on 2010-05-02
> **dino99 said:**
> some kind of sound tunneling

[http://www.tutcity.com/tutorial/control-sound-volume-with-actionscript.12619.html](http://www.tutcity.com/tutorial/control-sound-volume-with-actionscript.12619.html)
Thanks for the link, but I couldn't find a solution to the problem there...

---

### Post by kostkon on 2010-05-02
> **AaylaSecura said:**
> Mine's a little bit different:

[http://i41.tinypic.com/5p4z0j.png](http://i41.tinypic.com/5p4z0j.png)
[http://i44.tinypic.com/2yyuvf6.png](http://i44.tinypic.com/2yyuvf6.png)
Obviously, yes; you're using 9.04.

Install the *PulseAudio Device Chooser* utility and use the pulseaudio volume control.

Start your Flash game and then mute it from there.

---

### Post by kostkon on 2010-05-02
You can also add the device chooser utility to your startup programs (System &#8594; Administration &#8594; Sessions) and then easily right-click on its icon in the tray to access the pulseaudio volume control.

---

### Post by AaylaSecura on 2010-05-02
> **kostkon said:**
> Obviously, yes; you're using 9.04.

Install the *PulseAudio Device Chooser* utility and use the pulseaudio volume control.

Start your Flash game and then mute it from there.
Thank you. That worked perfectly :)

---

