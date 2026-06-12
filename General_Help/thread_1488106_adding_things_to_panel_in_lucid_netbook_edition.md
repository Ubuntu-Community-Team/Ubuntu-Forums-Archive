---
title: "adding things to panel in lucid netbook edition"
date: 2010-05-19
forum: General Help
---

### Post by w1ll1am on 2010-05-19
Hello does anyone know how to add add things to the panel in the netbook edition of lucid or make a new panel? Thanks

---

### Post by fabyouless on 2010-07-17
Have you found an answer to this, w1ll1am? I'm searching Google for an anwer and this popped up. Since this is a question and not an answer, i am hoping that there is at least a link pointing to the answer.

Please forgive my ignorance. I keep coming to the Ubuntu Forums to find answers on Lucid and am finding the forum posts to be less than my expectations.

---

### Post by Gaygerbil on 2010-07-27
[http://www.youtube.com/watch?v=8cS1ksvPNEU](http://www.youtube.com/watch?v=8cS1ksvPNEU)

---

### Post by kerry_s on 2010-07-27
> **w1ll1am said:**
> Hello does anyone know how to add add things to the panel in the netbook edition of lucid or make a new panel? Thanks

system-> main menu

---

### Post by Gaygerbil on 2010-07-30
> **kerry_s said:**
> system-> main menu

The's not at all what they're talking about.

Menu != Panel

---

### Post by insustancialidad on 2010-08-26
You can vote here in Ubuntu Brainstorm so that they fix this for good:
[http://brainstorm.ubuntu.com/ideatorrent/idea/24659](http://brainstorm.ubuntu.com/ideatorrent/idea/24659)

---

### Post by Neva on 2011-06-04
Thanks to denham2010's excellent tip at this thread: [http://ubuntuforums.org/showthread.php?t=1515732](http://ubuntuforums.org/showthread.php?t=1515732)

I managed to edit Ubuntu Netbook Remix 10.04 panel without switching to Gnome.

The file to edit is here:   ```
/var/lib/gconf/une.mandatory/%gconf-tree.xml
```Here are my   changes which got system monitor in the panel:
```
neva@neva-aone:/var/lib/gconf/une.mandatory$ diff %gconf-tree.xml gconf-tree.xml.original 
58,60d57
<                     <li type="string">
<                         <stringvalue>applet_7</stringvalue>
<                     </li>
151,164d147
<                 <dir name="applet_7">
<                     <entry name="object_type" mtime="1272540841" type="string">
<                         <stringvalue>bonobo-applet</stringvalue>
<                     </entry>
<                     <entry name="toplevel_id" mtime="1272540841" type="string">
<                         <stringvalue>top_panel</stringvalue>
<                     </entry>
<                     <entry name="panel_right_stick" mtime="1272540841" type="bool" value="true"/>
<                     <entry name="position" mtime="1272540841" type="int" value="1"/>
<                     <entry name="locked" mtime="1272540841" type="bool" value="true"/>
<                     <entry name="bonobo_iid" mtime="1272540841" type="string">
<                         <stringvalue>OAFIID:GNOME_MultiLoadApplet</stringvalue>
<                     </entry>
<                 </dir>
```Screen shot of the new UNR session:
[http://arcadia.anime.fi/~n/aspireone/UNR/UNR-sysmon-added.png]("http://arcadia.anime.fi/%7En/aspireone/UNR/UNR-sysmon-added.png")

Simple way to start with the terminal:
```
cd /var/lib/gconf/une.mandatory/
sudo cp %gconf-tree.xml gconf-tree.xml.original
sudo wget [http://arcadia.anime.fi/~n/aspireone/UNR/%25gconf-tree.xml]("http://arcadia.anime.fi/%7En/aspireone/UNR/%25gconf-tree.xml")
```Logout and login.
Right click on the new thin line in the top bar, choose preferences and adjust system monitor width to get it to draw correctly.

---

