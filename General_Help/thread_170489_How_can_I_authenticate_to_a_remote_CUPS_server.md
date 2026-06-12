---
title: "How can I authenticate to a remote CUPS server?"
date: 2006-05-04
forum: General Help
---

### Post by rvda on 2006-05-04
I'm trying to set up my Ubuntu 5.10 system as a printing client to a remote CUPS server. On my Ubuntu system I have stopped the cupsys service and I've put "ServerName remote_server" in /etc/cups/client.conf. Printing works, but only if I disable user authentication on the remote CUPS server. The preferred configuration for the remote CUPS server, however, is to require user authentication for all clients.
Is there any way I can make the printing client prompt for a username and password for the remote server. I know that gtklp can do this, but can the default printing client in Ubuntu/GNOME do this as well? BTW, what _is_ the default printing client in Ubuntu/GNOME and how could I change this to gtklp if it can't be made to behave as required?

---

### Post by rvda on 2006-05-10
I did some investigating and found that there is no default printing system in Ubuntu/GNOME. Basically every family of applications implements their own printing system. Here's what I've been able to find out about some of them so far:
1. OpenOffice has a simple but effective printing dialog that prompts for a user name and password. So this works in my preferred setup with an authenticating remote CUPS server.
2. Firefox (and likely Thunderbird as well) pipe to a print command which defaults to lpr (+ some options). Simply substituting gtklp for lpr (gtklp takes most of the options that lpr does) achieves what I need.
3. GNOME apps like Evolution and gedit use a print dialog that allows you to create a PDF document, create Generic PostScript output, or print to one of the remote CUPS printers. Printing to the remote CUPS printers fails silently if the remote CUPS server requires authentication. The solution is to choose Generic PostScript output, then for Location choose Custom and enter "gtklp". This solution came from this thread: [http://forum.ubuntu-fr.org/viewtopic.php?id=20519]("http://forum.ubuntu-fr.org/viewtopic.php?id=20519")

Hope this helps someone with similar requirements as mine. Now where do I file a bug against the GNOME print dialog that doesn't prompt for a password and silently fails to print?

---

