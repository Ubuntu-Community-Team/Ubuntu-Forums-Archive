---
title: "Ubuntu 12.04 doesn't shutdown anymore"
date: 2012-09-12
forum: General Help
---

### Post by randonname on 2012-09-12
Hello,
I'm a little desperate right now. I bought an Acer Aspire V5-571 and installed Ubuntu 12.04 on it 2 weeks ago. Everything was fine. After not using it for the last 2 weeks, I started it today but it doesn't shutdown anymore. Instead of shutting down, it reboots. What shall I do?

I appreciate any help, thanks very much!

---

### Post by Maro848 on 2012-09-12
I'm unsure how to completely fix the issue but I know that if you open the terminal then run "sudo shutdown now" without the quotes. You'll have to enter your password but then it should shut down. That should help until someone more experienced with this issue can get you more straightened away.

---

### Post by randonname on 2012-09-12
I tried different commands (sudo shutdown -h now, sudo shutdown -P now) but it didnt solve the problem. Also when I run the Ubuntu Live-CD (without installing anything) I can't properly shut it down.

---

### Post by offgridguy on 2012-09-12
Have you tried using log out prior to shutdown?
Do you have more than one user account?

A couple of thoughts here, if you have more than one user account, each must be logged out or it will not shutdown.  If someone has used your computer, even as a guest, they must be logged out.
Windows gives the option to shutdown without logging off individual users, ubuntu does not.

---

### Post by varunendra on 2012-09-13
> **offgridguy said:**
> A couple of thoughts here, if you have more than one user account, each must be logged out or it will not shutdown.  If someone has used your computer, even as a guest, they must be logged out...
In that case, the system wouldn't reboot also, while it does in OP's case. Reboot = full shutdown + re-start. :)

I have the same problem with my Asus X54C-261D laptop, albeit only when it is plugged into AC power. When on battery, it shuts down normally. Sometimes it also happens with Win7 I'm dual booting with, but rarely there. I doubt it to be some **acpi** related bug, but didn't find enough time yet to dig it. Besides, I don't mind unplugging for a sec. if it does the job. :)

---

### Post by offgridguy on 2012-09-13
> **varunendra said:**
> In that case, the system wouldn't reboot also, while it does in OP's case. Reboot = full shutdown + re-start. :):)

Thank you for your input. I realize that Reboot=full shutdown +re-start.
However it's easy to mistake the failure to shutdown as a full reboot if you
haven't experienced it before as the screen shuts down, then comes back on with
the password prompt. Only the icon in the upper right settings position indicates
that it is in shutdown mode.  I  was remiss in not mentioning this in my post.
Cheers.

---

### Post by chinmayzen on 2012-09-16
> **varunendra said:**
> In that case, the system wouldn't reboot also, while it does in OP's case. Reboot = full shutdown + re-start. :)

I have the same problem with my Asus X54C-261D laptop, albeit only when it is plugged into AC power. When on battery, it shuts down normally. Sometimes it also happens with Win7 I'm dual booting with, but rarely there. I doubt it to be some **acpi** related bug, but didn't find enough time yet to dig it. Besides, I don't mind unplugging for a sec. if it does the job. :)

I don't think that characterizes the problem. I've seen it happen a couple of times in the past week with the laptop unplugged (It's a Toshiba L-655). I've also encountered it once when the laptop was plugged in to AC power. So, this does seem to be a bug, but we've got to characterize it.

If anyone is familiar with the process, can ask/help us to characterize it. I'm sure there're a lot many people encountering this.

I'm going to try using the terminal for shutting down ubuntu for the next week.

---

### Post by chinmayzen on 2012-10-17
So this hasn't happened in the last 3-3.5 weeks. Maybe some update has done away with the problem? Does anyone still see it?

---

### Post by PowerBarry43 on 2012-10-17
what happens if you shutdown with

```
sudo init 0
```

?

Hope this helps!

Barry

---

### Post by sticksabuser on 2012-10-20
> **PowerBarry43 said:**
> what happens if you shutdown with

```
sudo init 0
```

?

Hope this helps!

Barry
Doing that actually shutsdown the laptop. Same laptop btw, with the same weird issue.

Update: it seems the above no longer seems necessary with the latest kernel updates. The Laptop now shuts down normally!

---

### Post by KozaG on 2013-01-18
I have this same shutdown problem with Dell Latitude D830. I'm using Ubuntu 12.04.

The strangest things is that sometimes does shot down normally but usually it doesn't.

---

