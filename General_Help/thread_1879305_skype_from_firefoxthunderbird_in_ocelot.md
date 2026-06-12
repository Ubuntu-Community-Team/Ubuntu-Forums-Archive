---
title: "skype from firefox/thunderbird in ocelot"
date: 2011-11-11
forum: General Help
---

### Post by linuxgeoff on 2011-11-11
I just cannot get get direct click-on dialing to work in 11.10 using telify or similar programs.  I have it working fine on an old machine with 10.04.

The main issues ***seems*** to be that skype does not install any protocols (action handlers).  I've scoured the web; I've found old perl and python scripts and built the handlers; I've modified the keys in firefox about:config, and I still get "Bo program is installed which registered itself for the protocol" error

I've searched everywhere and I've yet to find any solid fix to this problem; I've not even found any evidence that anyone has this working. So, two questions for the community:

1) does anyone have direct click-on dialing from firefox through skype working in 11.10?

2) Can anyone describe a definitive solution and/or problem solving approach?

Thanks, all

---

### Post by linuxgeoff on 2011-11-18
bump! (if that's not bad etiquette..)

Has anyone got this working?  What more should I provide to help define the problem?

Thx,  Geoff

---

### Post by linuxgeoff on 2011-12-16
Anyone?  Please?

I know others have the same problem.

---

### Post by linuxgeoff on 2012-01-11
bump

---

### Post by linuxgeoff on 2012-01-20
I think I solved it, and it's down to a change in the way that Gnome catalogs Applications. However, it's probably not elegant and if any of you maistros can help improve it, we'd all be grateful:

1) list a new .Desktop file in /usr/share/applications/defaults.list by adding the following line:
x-scheme-handler/skype=firefox-skype.desktop

2) create a firefox-skype.dedsktop file in /usr/share/applications with the following lines:
[Desktop Entry]
Encoding=UTF-8
Name=Skype Action Handler
Comment=Call from Skype
GenericName=Skype Client
Exec=/usr/local/bin/skype_action_handler_1.0.pl %u  
Terminal=false
X-MultipleArgs=false
Type=Application
Icon=skype
Categories=Application;Network;
MimeType=x-scheme-handler/skype;

#replace /usr/local/bin/skype_action_handler_1.0.pl with your own file and path name
and it seems to work

---

### Post by deejaylight on 2012-02-23
hey!
Same problem.
This solution work fine in ubuntu 11.04 but in ubuntu 11.10 does not
I'm getting an error when trying to run make command
can anyone tell where can I download the skype_action_handler_1.0?

---

