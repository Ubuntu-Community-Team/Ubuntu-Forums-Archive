---
title: "Building Desktop Drapes in Karmic"
date: 2009-12-23
forum: General Help
---

### Post by stevebu56 on 2009-12-23
I'm trying to build Desktop Drapes in Karmic with the following commands & I am running into some build issues.  Here are my steps.  I would appreciate any help. 

sudo apt-get source drapes 
sudo apt-get build-dep drapes 
cd drapes-0.5.2
./configure 
make 

I get the following errors.  I'm guessing some namespaces moved around or ones need to be included? 

---------------------------------------------------------------------
Making all in drapes
make[1]: Entering directory `/home/sburke/sandbox/drapes/drapes-0.5.2/drapes'
/usr/bin/gmcs -debug  -r:System.Xml -r:Mono.Posix -pkg:gconf-sharp-2.0 -pkg:glade-sharp-2.0 -pkg:gnome-vfs-sharp-2.0 -resource:../data/drapes.glade,drapes.glade  \
	-unsafe+ -target:exe -out:"drapes.exe" \
	./AssemblyInfo.cs ./panelapplet/*.cs ./About.cs ./Applet.cs ./AppletWidget.cs ./ConfigMenuWidgets.cs ./ConfigMenu.cs ./Main.cs ./Settings.cs ./Traylib.cs ./Wallpaper.cs ./WpList.cs
**./panelapplet/ChangeBackgroundHandler.cs(11,30): error CS0234: The type or namespace name `PanelAppletBackgroundType' does not exist in the namespace `Gnome'. Are you missing an assembly reference?**
./panelapplet/PanelApplet.cs(463,26): warning CS0109: The member `_Gnome.PanelApplet.SetupMenuFromResource(System.Reflection.Assembly, string, _Gnome.BonoboUIVerb[])' does not hide an inherited member. The new keyword is not required
./AppletWidget.cs(38,25): warning CS0612: `Gtk.Tooltips' is obsolete
**./AppletWidget.cs(39,23): error CS0234: The type or namespace name `IconTheme' does not exist in the namespace `Gnome'. Are you missing an assembly reference?**
./ConfigMenu.cs(34,13): warning CS0612: `Gtk.Tooltips' is obsolete
[B]./Main.cs(49,63): error CS0234: The type or namespace name `Program' does not exist in the namespace `Gnome'. Are you missing an assembly reference?
./Main.cs(50,35): error CS0234: The type or namespace name `Client' does not exist in the namespace `Gnome'. Are you missing an assembly reference?
./Main.cs(190,52): error CS0234: The type or namespace name `SaveYourselfArgs' does not exist in the namespace `Gnome'. Are you missing an assembly reference?[/B]
Compilation failed: 5 error(s), 3 warnings
make[1]: *** [drapes.exe] Error 1
make[1]: Leaving directory `/home/sburke/sandbox/drapes/drapes-0.5.2/drapes'
make: *** [all-recursive] Error 1

---

### Post by rabdoel on 2010-01-09
why are you building it from source ?

just get the package from synaptics and install it ?

---

