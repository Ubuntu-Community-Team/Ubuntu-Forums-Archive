---
title: "How to drop the firewall from a remote terminal?"
date: 2011-11-01
forum: General Help
---

### Post by AlexBooton on 2011-11-01
Hi,

I manage a remote server using tools like VNC, Webmin, Hamachi and putty (in order to get a remote terminal).

Everything was working fine until a power failure over the weekend. When the system came back up I find myself unable to connect via Hamachi and VNC. 

I can still connect via putty and Webmin but I need VNC for the GUI.

This is U11.04.  Is it possible it was upgraded automatically and, after the reboot, the firewall settings have changed?

How can I temporarily drop the firewall from a terminal so I can connect via VNC and see what's going on?

And, just to be safe, how can I restore the firewall from the terminal?

Thanks

---

### Post by Dangertux on 2011-11-01
What did you use to create the firewall? An iptables script, ufw or something like firestarter?

If you aren't sure it would make me wonder if this server was yours.

---

### Post by AlexBooton on 2011-11-01
> **Dangertux said:**
> What did you use to create the firewall? An iptables script, ufw or something like firestarter?

If you aren't sure it would make me wonder if this server was yours.

Yes, it's really mine!  If it wasn't, I wouldn't be able to get root access via putty.

I'm using Firestarter.  That's the main reason I need the GUI.  I.E. to modify the rules if that's necessary.

But what I don't understand is how the rules could have changed.

I need help.

---

### Post by Dangertux on 2011-11-01
> **AlexBooton said:**
> Yes, it's really mine!  If it wasn't, I wouldn't be able to get root access via putty.

I'm using Firestarter.  That's the main reason I need the GUI.  I.E. to modify the rules if that's necessary.

But what I don't understand is how the rules could have changed.

I need help.

Ok well if you're using firestarter (which I really dont't recommend, for a server interacting with iptables directly is preferable)

```

sudo firestarter -p

```should stop the firewall

```

sudo firestarter -s 

```or 

```

sudo firestarter --start-hidden

```will start the firewall and start it without the gui respectively.

Also : having root access via ssh does not necessarily mean the server is yours.

I would also recommend running the VNC service locally and connecting to it via an SSH tunnel, VNC itself is horridly easy to crack.

Anyway good luck. Keep in mind if the server rebooted the firewall rules probably didn't change, what probably happened is the VNC service was not restarted.

---

### Post by AlexBooton on 2011-11-01
> **Dangertux said:**
> Ok well if you're using firestarter (which I really dont't recommend, for a server interacting with iptables directly is preferable)

```

sudo firestarter -p

```should stop the firewall

```

sudo firestarter -s 

```or 

```

sudo firestarter --start-hidden

```will start the firewall and start it without the gui respectively.

Also : having root access via ssh does not necessarily mean the server is yours.

I would also recommend running the VNC service locally and connecting to it via an SSH tunnel, VNC itself is horridly easy to crack.

Anyway good luck. Keep in mind if the server rebooted the firewall rules probably didn't change, what probably happened is the VNC service was not restarted.

It worked!!!

Many thanks!

---

### Post by Dangertux on 2011-11-01
Glad it worked out, please don't think I was trying to accuse you of something. It's just when people ask how to disable a security feature on a system, you have to be careful. Since you never know if their intentions are good or not.

---

### Post by AlexBooton on 2011-11-01
> **Dangertux said:**
> Glad it worked out, please don't think I was trying to accuse you of something. It's just when people ask how to disable a security feature on a system, you have to be careful. Since you never know if their intentions are good or not.

I understand and sincerely appreciate your help.

AB

---

