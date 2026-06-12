---
title: "restore wine from Meerkat to Ocelot?"
date: 2012-02-15
forum: General Help
---

### Post by qwertyjjj on 2012-02-15
I have a backup of wine from a Meerkat distro.
Can I just copy the /home/.wine folder to Ocelot and get it working again?
Are there any other folders to consider?

Edit:  I cannot see .wine in the Ocelot distro - am looking at the /home/user/ folder
Edit2: just did winecfg to create the .wine folder and then copied the .wine from the backup. However, I cannot get to the wine application I used to use. Any ideas on how to access it?

I am trying to run this program but it won;t start: To start MetaTrader 4 from the menu of ANY window manager, one can use the following sequence of commands:

'cd /home/user/.wine/drive_c/'Program Files'/MTrader4/; wine ./terminal.exe', where /home/user is the home directory of the current user.

[http://articles.mql4.com/416](http://articles.mql4.com/416)

[B]Downloads$ wine MT4_set_up.exe
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls" (6.0.0.0)[/B]

winetricks
------------------------------------------------------
wine cmd.exe /c echo '%ProgramFiles%' returned unexpanded string '%ProgramFiles%' ... can be caused a corrupt wineprefix, an old wine, or by not owning /home/jack/.wine
------------------------------------------------------

---

