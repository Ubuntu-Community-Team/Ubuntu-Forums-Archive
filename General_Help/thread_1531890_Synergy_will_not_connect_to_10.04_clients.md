---
title: "Synergy will not connect to 10.04 clients"
date: 2010-07-15
forum: General Help
---

### Post by jeebustrain on 2010-07-15
I've been using synergy for a while and love it. I recently upgraded both of my desktop PCs at home from 9.10 to 10.04 (both x64 ubuntu studio). Now, Synergy doesn't appear to want to work. I've tested with both the cli command referencing a config file on the server and using quicksynergy on both machines and it just doesn't connect. I verified on my "server" that synergy is listening on port 24800 (can telnet to that port from the client machine). I manually disabled the firewall on both machines as well and it doesn't seem to make a difference. It never gives an error on the client, it just never makes the connection. I've tested this with 2 separate 10.04 clients. I also brought one of these boxes (a laptop) to work where I use Synergy between 2 windows boxes. It won't connect to those either. 

I've tried connecting both using hostname and IP address (both worked in the past on 9.10) and neither work.

Does anyone use synergy in Lucid?

---

### Post by Thomas_Bates on 2010-08-15
I'm having the same problem, sort of. I get a time out error when trying to connect using an IP, and a different error when trying to connect using the hostname

Bump.

---

### Post by Aearenda on 2010-08-15
I use it every day with 10.04, no problems - but I use 32 bit, not 64.

---

### Post by howefield on 2010-08-15
> **Thomas_Bates said:**
> I'm having the same problem, sort of. I get a time out error when trying to connect using an IP, and a different error when trying to connect using the hostname

Bump.

I doubt it is a 10.04 issue or 64 bit.

Try posting the error(s) and give someone half a chance of helping you.

---

### Post by thinkinhurtz on 2010-08-24
This is a setup for Windows 7 - 10.04 that has worked for me:

# Install Synergy on both Ubuntu and Windows
Ubuntu: Run the command &#8220;sudo apt-get install synergy&#8221;
Windows: Download the .exe program from SourceForge.
# As root on the Ubuntu machine, create an /etc/synergy.conf file with the command &#8220;sudo vi /etc/synergy.conf&#8221;

    section: screens
    ubuntu:
    windowspc:
    end

    section: aliases
    windowspc:
    192.168.1.101
    end

    section: links
    ubuntu:
    left = windowspc
    windowspc:
    right = ubuntu
    end

    section: options
    screenSaverSync = false
    # My KVM uses Scroll Lock to switch screens, so set the
    # hotkey to lock the cursor to the screen to something else
    keystroke(f12) = lockCursorToScreen(toggle)
    end 

There are several things to note in this configuration file:
- If one of your machines doesn&#8217;t have a DNS name, you can use the IP address of that machine. The &#8220;aliases&#8221; section lets you do that in a clean way. To find your IP address on Windows XP, do Start->Run, enter cmd, and type &#8220;ipconfig /all&#8221;. On Linux/Ubuntu, use &#8220;ifconfig&#8221; to find your machines&#8217;s IP address.

- In the &#8220;links&#8221; section, you have to define both behaviors: going offscreen-left on the Ubuntu (right) machine, and going offscreen-right on the Windows (left) machine. In theory you can create really weird mappings, but keeping it simple is usually best.

- The &#8220;screenSaverSync = false&#8221; command says not to link the screensavers of the two machines.

- Synergy normally uses the &#8220;Scroll Lock&#8221; key as a toggle that prevents your mouse from leaving the screen. I have a KVM switch that uses the Scroll Lock key, so I redefined the &#8220;lock Cursor to Screen&#8221; key to a harmless button (f12).
# Make sure that the Ubuntu configuration file is world-readable. Run the command &#8220;sudo chmod a+r /etc/synergy.conf&#8221; to do that.
# Next, test the server and client and make sure that everything works. On the Ubuntu server, run &#8220;synergys -f --config /etc/synergy.conf&#8221;

---

