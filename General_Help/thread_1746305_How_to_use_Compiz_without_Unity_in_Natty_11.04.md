---
title: "How to use Compiz without Unity in Natty 11.04"
date: 2011-05-01
forum: General Help
---

### Post by Emilie on 2011-05-01
So I was really excited to try the new Unity interface and installed 11.04 today.  I was disappointed with how slow it was and how difficult it is to manage your desktop with multiple windows open.  Anyway, critiques aside, I wanted to go back to normal gnome.

They problem is that I usually use Compiz on my gnome desktop, if you choose "Classic Ubuntu" from the login screen (to avoid Unity), it starts loading a regular gnome session, however, as soon as Compiz gets loaded, it starts up Unity!  It took me a while to figure out what was going on and how to fix it.

I use fusion-icon, so if you don't have that, you may need to install it.

**1. Turn off unity once you are in a classic login**
- choose "Classic Ubuntu" from the login screen
- if you are like me, this will still load Unity as soon as compiz gets loaded
- now, open a terminal window
- run "fusion-icon"
- this will reload fusion-icon, and restart compiz, which will reload Unity
- now, in the terminal, do "ctrl-c"
- this will force close compiz and therefore Unity.  You should see you gnome-panel back, with the fusion-icon in the corner

**2. Turn metacity on**
- right-click on the fusion-icon, choose "choose window manager" and select metacity
- now you will have normal metacity windows

**3. Disable Unity plugin**
- right-click on the fusion-icon, choose "Settings Manager"
- under "Desktop" you should see the "Ubuntu Unity Plugin", disable it
- at the very bottom you should also see "Unity MT Grab Handles", I disabled it, I haven't ever seen the handles so don't know what they are.
- also, all of your old compiz config settings will be gone :( you'll have to set them all up again.

**4. Re-enable Compiz**
- now, you can right-click on the fusion-icon and choose "Choose window manager" again.
- choose compiz
- tada! compiz with now Unity.

Logout and make sure Unity doesn't pop-up again.

Hope this helps someone!

---

### Post by lcason on 2011-05-01
:( Be careful with the "disable Unity plugin" action. I did that an hour ago on my 11.04 machine (not from your suggestion--tried it on my own) that was upgraded from 10.10, and ended up with a blank UI! Nothing but a desktop background and a right-click mouse menu. 

Then I found a post here to install gnome3 as an alternative to Unity. I went through that and did get gnome3 installed, but can't login. Get error "Could not update ICEauthority /home/lee/.ICEauthority". So, looks like my next step is to reinstall 10.10 from scratch and avoid 11.04 until it is less buggy.

---

### Post by Emilie on 2011-05-02
I can't be sure but that sounds like it is loading compiz but not with 3d direct rendering.  Could you try something like ctrl-alt-f1, login in as root, do a pkill compiz (or ps -A, find the compiz processes, and kill them), then ctrl-alt-f7 back to X and run metacity or something (via gnome-terminal or alt-f2).

Or X loaded but not your gnome session?

No idea, works good for me but I knew that 3d direct rendering was working before I disabled the plugin and that my "classic" gnome desktop was loading fine (I could see my gnome-panels, etc. briefly) before the Unity thing plopped on top.

Good luck fixing it!

On that note though, Ubuntu really needs to think about ways to downgrade an installation without having to re-install!

---

