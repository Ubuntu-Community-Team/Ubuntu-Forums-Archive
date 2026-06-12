---
title: "Gnome-RDP"
date: 2009-07-15
forum: General Help
---

### Post by jalexakis on 2009-07-15
Having failed to connect my Ubuntu 6.03 machine to the win 2008 terminal server using the Terminal server client (posted on other thread) i thought i´d try gnome-rdp. 

And it worked, kinda. Problem is, using gnome-rdp the terminal server creates sessions only for users that belong to the local Admin-group, else session creation is denied. I don´t have the problem with either Windows RDP-client or Terminal Server Client.

Does anyone know what this is about ?

Thanks for the help ):P

---

### Post by alphacrucis2 on 2009-07-15
> **jalexakis said:**
> Having failed to connect my Ubuntu 6.03 machine to the win 2008 terminal server using the Terminal server client (posted on other thread) i thought i´d try gnome-rdp. 

And it worked, kinda. Problem is, using gnome-rdp the terminal server creates sessions only for users that belong to the local Admin-group, else session creation is denied. I don´t have the problem with either Windows RDP-client or Terminal Server Client.

Does anyone know what this is about ?

Thanks for the help ):P

6.03 ? What is that. I recall there was 6.06 & 6.10.

---

### Post by jalexakis on 2009-07-15
> **alphacrucis2 said:**
> 6.03 ? What is that. I recall there was 6.06 & 6.10.

I meant 9.03, sorry :^o

---

### Post by chriskin on 2009-07-15
> **jalexakis said:**
> I meant 9.03, sorry :^o
i suspect there is not 9.03 either but le'ts not waste time and leave this to someone who knows to answer

---

### Post by stinger30au on 2009-07-15
have you got automatic login disabled??

make sure you do and manually type in the user name/password then ubuntu connects to the windows rdp session and you should be cooking with gas

---

### Post by jalexakis on 2009-07-15
> **stinger30au said:**
> have you got automatic login disabled??

make sure you do and manually type in the user name/password then ubuntu connects to the windows rdp session and you should be cooking with gas

Automatic login is disabled. Each user has to enter his Username/Password at the Win2008 login prompt. And everyone gets to do that, too. Only, those that aren local admins on the TS only get an  error (windows-side) stating the session could not be created.

---

