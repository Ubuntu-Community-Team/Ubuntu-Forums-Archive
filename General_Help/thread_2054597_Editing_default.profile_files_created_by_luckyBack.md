---
title: "Editing default.profile files created by luckyBackup"
date: 2012-09-07
forum: General Help
---

### Post by dragonfly41 on 2012-09-07
I've started using  **[COLOR=Navy]luckyBackup[/COLOR]** (installed from Synaptic Package Manager) for rsync/ssh between localhost and AWS EC2/S3 instances.   It is a very useful tool.

The batch of rsync Tasks are saved in a file **[COLOR=Navy][name of profile].profile[/COLOR]**.   The default is **[COLOR=Navy]default.profile[/COLOR]**.

If variables change over time (e.g. dynamic IP addresses or source/destination folders) instead of going through each Task batched in the GUI Task List and changing fields in the Task Properties - I would like to simply manually edit the *.profile file using a find and replace script.

So what editor is suggested for this purpose?

I can view the file default.profile as text (by just opening default.profile in a text editor)  but it is not in any format which is easy to edit by string find+replace.  I know that it's not the best practice to hack system files but I don't see any other way of introducing changes .. other than going through the entire Task List per profile. There could be quite a nunber to edit.  So I want to have a script to process the default.profile .. then launch luckyBackup with the edited profile(s) .. or use in console mode.

---

### Post by dragonfly41 on 2012-09-07
Apparently it's much simpler than I thought .. using sed ..

this is the general syntax ...
sed -i 's/this/tothis/' file

and here is an example of changing AWS EC2 Host IP address [COLOR=Red]xx.xxx.xxx.xx[/COLOR] to [COLOR=Blue]zz.zzz.zzz.zz[/COLOR]  in default.profile file exported by luckyBackup  ...

sed  -i 's/@.e.c.2.-.[COLOR=Red]x.x.-.x.x.x.-.x.x.x.-.x.x..[/COLOR].e.u.-.w.e.s.t.-.1...c.o.m.p.u.t.e...a.m.a.z.o.n.a.w.s...c.o.m./@.e.c.2.[COLOR=DarkGreen]-.[COLOR=Blue]z.z.-.z.z.z.-.z.z.z.-.z.z.[/COLOR].[/COLOR].e.u.-.w.e.s.t.-.1...c.o.m.p.u.t.e...a.m.a.z.o.n.a.w.s...c.o.m./'     ~/luckybackup_profiles/default.profile

I viewed the default.profile content in text editor to get the general layout.

So with sed "find and replace" I hope to be able to edit luckyBackup profile templates to be imported as Task Lists.

=========================

[COLOR=DarkRed][Edit]

Later I found from posting on luckyBackup forum that I had been using an old version (0.4.1) of luckyBackup from Synaptic Package Manager.  The latest version (0.4.7) of luckyBackup has simple text format for *.profile files (no longer in hex format with dots between characters) and so parsing and editing by sed is much easier and less error prone.

[/COLOR]=========================

---

