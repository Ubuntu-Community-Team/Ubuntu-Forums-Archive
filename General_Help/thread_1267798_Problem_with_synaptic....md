---
title: "Problem with synaptic..."
date: 2009-09-16
forum: General Help
---

### Post by Fred Bear on 2009-09-16
Every time I open up synaptic, I get this error message: "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. E: _cache->open() failed, please report." Okay, I open up the terminal as root & run that 'dpkg --configure -a' command and, for some reason, there is always this error where it is checking the 'emphasis' source over and over again. Here is the terminal output:
    
    
    
    root@lestermaryann:/home/lestermaryann# dpkg --configure -a
    Setting up e17-svn (1.2.4-4) ...
    
    ---------------------------- Easy_e17.sh 1.2.4.2-OzOS --------------------------
      Developers:      Brian 'morlenxus' Miculcy
                       David 'onefang' Seikel
      Contributors:    Tim 'amon' Zebulla
                       Daniel G. '_ke' Siegel
                       Stefan 'slax' Langner
                       Massimiliano 'Massi' Calamelli
                       Thomas 'thomasg' Gstaedtner
                       Roberto 'rex' Sigalotti
    
    ----------------------------- Current Configuration ----------------------------
      Install path:    /opt/e17
      Source path:     /var/cache/e17_src
      Source url:      [http://svn.enlightenment.org/svn/e/trunk](http://svn.enlightenment.org/svn/e/trunk)
      Logs path:       /tmp/easy_e17/install_logs
    
      Packages:        eina eet evas ecore efreet embryo edje epsilon esmart emotion etk etk_extra ewl exml enhance e_dbus e entrance edje_editor elicit elitaire enna enthrall emphasis empower emprint ephoto estickies exhibit expedite exquisite extrackt eyesight e_phys rage alarm bling calendar cpu deskshow diskio drawer efm_nav efm_path emu exalt-client execwatch flame forecasts iiirk language mail mem moon mpdule net news notification penguins photo places rain screenshot slideshow snow systray taskbar tclock tiling uptime weather winselector wlan
      Skipping:        esmart enhance exml imlib2 edb edje_editor edje_player edje_viewer emotion entrance eclair evfs evolve elicit elitaire emphasis empower engycad entrance_edit_gui entropy ephoto estickies expedite exquisite extrackt engage enthrall exalt-client exhibit rage emu flame moon news penguins rain snow language photo efm_path efm_nav e_phys mpdule notification b_and_w 
    
      Source conflict: solve automatically
      Script action:   install
    --------------------------------------------------------------------------------
    
    -------------------------------- Build phase 1/3 -------------------------------
    - running some basic system checks
    - source checkout/update
    --------------------------------------------------------------------------------
    
    
    ------------------------------- Basic system checks ----------------------------
    - creating script dirs ....... ok
    - 'automake' available ....... ok
    - 'gcc' available ............ ok
    - 'make' available ........... ok
    - 'svn' available ............ ok
    - build-user ................. root
    - adding path to env ......... ok
    - checking lib-path in ldc ... ok (/etc/ld.so.conf.d/e17.conf)
    - setting compile options .... ok
    --------------------------------------------------------------------------------
    
    ----------------------------- Source checkout/update ---------------------------
    - updating sources (please wait, this won't output much) ...
    Checking e source ... At revision 42506.
    Checking ecore source ... At revision 42506.
    Checking e_dbus source ... At revision 42506.
    Checking edje source ... U    edje/src/lib/edje_private.h
    U    edje/src/lib/edje_edit.c
    U    edje/src/lib/Edje.h
    U    edje/src/lib/Edje_Edit.h
    Updated to revision 42506.
    Checking edje_editor source ... At revision 42506.
    Checking eet source ... At revision 42506.
    Checking efreet source ... At revision 42506.
    Checking eina source ... At revision 42506.
    Checking elicit source ... At revision 42506.
    Checking elitaire source ... At revision 42506.
    Checking embryo source ... At revision 42506.
    Checking E-MODULES-EXTRA source ... At revision 42506.
    Checking emotion source ... At revision 42506.
    Checking emphasis source ... svn: REPORT request failed on '/svn/e/!svn/vcc/default'
    svn: Target path does not exist
    svn: REPORT request failed on '/svn/e/!svn/vcc/default'     
    svn: Target path does not exist
    svn: REPORT request failed on '/svn/e/!svn/vcc/default'     
    svn: Target path does not exist
    svn: REPORT request failed on '/svn/e/!svn/vcc/default'     
    svn: Target path does not exist
    svn: REPORT request failed on '/svn/e/!svn/vcc/default'     
    svn: Target path does not exist
    svn: REPORT request failed on '/svn/e/!svn/vcc/default'     
    svn: Target path does not exist
    svn: REPORT request failed on '/svn/e/!svn/vcc/default'     
    svn: Target path does not exist
    svn: REPORT request failed on '/svn/e/!svn/vcc/default'     
    svn: Target path does not exist
    svn: REPORT request failed on '/svn/e/!svn/vcc/default'     
    svn: Target path does not exist
    svn: REPORT request failed on '/svn/e/!svn/vcc/default'     
    svn: Target path does not exist
    svn: REPORT request failed on '/svn/e/!svn/vcc/default'     
    svn: Target path does not exist
    FAILED! Next attempt 12 in 265 seconds
    
It just keeps on checking the emphasis source over and over again. Is there any way it could possibly skip that one and go onto the next one? Anyone's help would be appreciated. Thanks.:)

---

### Post by Fred Bear on 2009-09-16
Anyone?

---

### Post by Fred Bear on 2009-09-16
Well, I fixed the problem all on my own. The whole problem was the result of this little text file called 0000 which was located at /var/lib/dpkg/updates. I just deleted that file & everything was all fine again. Thank you everyone for your prompt replies. NOT!!!!!!!

---

### Post by JasonLean on 2009-10-08
Thank u SO LOT!!! :-) I thought I was the only newbie to install e 17. The only difference was that in my case easyE17 could not download epsilon. Deleting 0000 solved the prob. Who could even think? -)

---

