---
title: "Help with screensaver"
date: 2010-10-27
forum: General Help
---

### Post by johnmay on 2010-10-27
Speaking of the Screensaver,  I would like to find where the file that controls it is. If there is any idea info would be appreciated. 

I have a double monitor, and when the screensaver is on it projects different images to each monitor. The desktop backgroud program uses the same picture for each monitor. I would like to use the screensaver code to run my desktop background 

You know for kids.
Found it:

~/home/*user*/.gconf/apps/gnome-screensaver

---

### Post by johnmay on 2010-10-28
Is there a gnome expert out there who could help answer the question? 

Here is the gconf that runs the screensaver: 

<?xml version="1.0"?>
<gconf>
    <entry name="themes" mtime="1288202264" type="list" ltype="string">
        <li type="string">
            <stringvalue>screensavers-cosmos-slideshow</stringvalue>
        </li>
    </entry>
    <entry name="mode" mtime="1288202264" type="string">
        <stringvalue>single</stringvalue>
    </entry>
</gconf>

And here is the one that point to the background:

<?xml version="1.0"?>
<gconf>
    <entry name="primary_color" mtime="1288239702" type="string">
        <stringvalue>#2c2c00001e1e</stringvalue>
    </entry>
    <entry name="secondary_color" mtime="1288239702" type="string">
        <stringvalue>#2c2c00001e1e</stringvalue>
    </entry>
    <entry name="picture_filename" mtime="1288239702" type="string">
        <stringvalue>/usr/share/backgrounds/cosmos/background-1.xml</stringvalue>
    </entry>
    <entry name="color_shading_type" mtime="1288239702" type="string">
        <stringvalue>solid</stringvalue>
    </entry>
    <entry name="picture_options" mtime="1288239702" type="string">
        <stringvalue>zoom</stringvalue>
    </entry>
</gconf>

So i guess really I need to find the themes file / folder and monkeyboot there for a while

Any ideas?

---

### Post by johnmay on 2010-11-01
Seriously! 

Does anyone know where the conf file that runs the screensaver is located?


Thanks!

---

### Post by johnmay on 2010-11-13
I ma interested in the file to change how my desktop works. I know that there are suggestions about the actual desktop, but the screen saver is so much better!

Thanks!

---

### Post by cariboo on 2010-11-13
This is a support request, not a testimonial or an experience, moved to General Help.

---

