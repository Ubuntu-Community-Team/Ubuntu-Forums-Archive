---
title: "Play on Linux Stopped Working"
date: 2011-04-03
forum: General Help
---

### Post by dlemos on 2011-04-03
Hi all

I've downloaded Wine and PlayOnLinux and installed Google chrome. Everything fine so far. But When I installed Photoshop CS4, I am unable to run Photoshop or Chrome. When I click Run, nothing happens.

Any ideas?

Thank you.

---

### Post by tredegar on 2011-04-03
This doesn't *really* answer your Q, but I'm trying to be helpful....

Some things that run on win (photoshop) just do not play nicely with linux, though those fine people developing wine are doing their very best.

A more relaxed mindset is to think "This, this and this works well on linux (mostly everything to to with the WWW), so I'll use linux for those things".

Some applications (Eg photoshop) do not play well with linux. Even with wine. They may never do so. So, just use windows if you really need photoshop, and cannot get to grips with **gimp**.

Use the right tool(s) for the job ;)

**chromium-browser** (very like google chrome, but without the security, and personal data-gathering issues) is available from the ubuntu repositories. Just install it by using System - Administration - Synaptic and search for chromium. It works fine (I'm using 10.04)

---

### Post by 311005901 on 2011-04-03
It looks like one (or more) of your programs has crashed and is still running in the background. In PlayInLinux, click on "Tools" and select "Kill wineserver process". After that, you might want to simulate a Windows reboot.

Hopefully that will solve it.

---

### Post by dlemos on 2011-04-04
"Kill wineserver process"

I don't see that option :/

It's not on tools or in "application configuration"
The options I see on tools are:
[LIST]
[*]Manage wine versions
[*]Run a non official script
[*]PlayOnLinux dialog
[*]Autorun
[/LIST]

On application configuration there are other options. I've attached an image with the options (name: "options" ).


A dialog box showed up the first time I tried to run photoshop. I've also uploaded a screenshot with it ("firstRun"). But now nothing this dialog box doesn't appear
:/

---

### Post by 311005901 on 2011-04-05
Try "Kill All the Prefix Processes" and then reopen the programs from the PlayOnLinux manager.
 Sorry I told you something different in the other post. I should have double checked...

---

### Post by dlemos on 2011-04-05
Nope, doesn't work :/

Well, Gimp seems pretty similar...I think I'll take up the challenge and try to use Gimp:)

Anyway, thank you for your help:)

---

