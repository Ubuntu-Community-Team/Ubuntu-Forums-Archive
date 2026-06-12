---
title: "Moving Ubuntu Install To New PC?"
date: 2011-10-20
forum: General Help
---

### Post by Joshwaa on 2011-10-20
I'm planning on getting a new PC soon and I want to be able to have my exact Ubuntu installation copied over to it so not to have to install everything again and set everything up such as my mysql servers, ruby/rails, etc. etc.

Is there any way I could do this?

---

### Post by drofart on 2011-10-20
> **Joshwaa said:**
> I'm planning on getting a new PC soon and I want to be able to have my exact Ubuntu installation copied over to it so not to have to install everything again and set everything up such as my mysql servers, ruby/rails, etc. etc.

Is there any way I could do this?
  Just back up using [this]("http://ubuntuforums.org/showthread.php?t=35087") tutorial . copy back up & restore using live cd or usb on ur new computer.


sona.

---

### Post by Mark Phelps on 2011-10-20
Another way to do it would be to use Clonezilla to clone the current drive to the new drive.  Then, just replace the old drive with the new -- and you should be good to go.

One caveat ... if you have installed restricted drivers, and the old hardware is not present on the new PC, that could pose some problems, especially if they are video drivers.

---

