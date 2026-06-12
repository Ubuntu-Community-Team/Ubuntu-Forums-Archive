---
title: "Are Ubuntu &amp; Kubuntu fighting each other?"
date: 2006-01-31
forum: General Help
---

### Post by back2ubuntu on 2006-01-31
Hello,

I was running ubuntu 5.10 with gnome but I missed KDE that I'd been using for many years.

So I installed kubuntu-desktop ("on top of ubuntu").

Unfortunately I run into various annoying troubles:

i) The login screen magner is no longer avaible, neither under ubuntu nor kubuntu. As a consequence, I can not use the gnome login manager, which I find much better than the blue kubuntu tiny window with tiny fonts.
In addition, I can no longer allow for a root session.

The same problem with Art gnome

ii) This is the most important issue to me: Most of my KDE applications (in KDE desktop) have very small fonts. Is there a way to change the fonts on the task bar, menus, text below icons, etc, in all kde applications ?

iii) Keffeine, gxine, no longer working properly!?

Any ideas to fix these prbs would be well appreciated.
Many thanks in advance.

lnp

---

### Post by rwabel on 2006-01-31
that sounds strange. I'm on dapper, but I was using ubuntu and did add kubuntu. I don't have your behavior. GDM was still my Desktop Manager...well I did change it now to check out KDM. :-)
My problem is that someone konqueror is now the browser that liferea is using, even thought I set firefox in liferea and in GNOME default browser is firefox. :-)

I've also problem with the kde sound server. That's an annoying thing I need to look deeper into.

you can change fonts, style etc under system settings->appearance

I don't have problems with these media players at all

---

### Post by RavenOfOdin on 2006-01-31
I had that exact same problem earlier today. . .

1) KDE, under System Settings, kept on crashing with SIGSEGV.
2) KDM took its settings and superimposed them on to GNOME. This resulted in such things as not being able to get into the "Login Screen Setup" and bold font in the then-Kubuntu splash screen.
3) The only way I could get GDM and the "Login Screen Setup" to show up again, was to kill KDM through the services tab (yeah, I know, not a good habit) and enter terminal mode to start the former.
4) After more wrangling and minor problems, I found that my Internet connection wouldn't start up, and the bootsplash screen stopped for 45 seconds at "Configuring Network Devices."

I had to take everything related to KDE out through the Synaptic, and reinstall my DHCP through the main disk, before the Internet would come back up.

It was weird. . . :S

---

