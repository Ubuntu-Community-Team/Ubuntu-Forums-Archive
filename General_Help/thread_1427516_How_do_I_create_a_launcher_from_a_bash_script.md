---
title: "How do I create a launcher from a bash script?"
date: 2010-03-11
forum: General Help
---

### Post by jan schoubo on 2010-03-11
A simple question:

How do I automate the creation of a launcher from a bash script?

I can easily create my launcher by drag and drop or right-clicking on
the menu panel, but I would like to fully automate this from a bash script.
I suppose it is a Gnome question rather than a general Ubuntu question, 
but all searches typically ends explaining how to create a launcher that
runs a bash script, and it is kind of the other way round I want :D

Any hints or HOWTO's will be much appreciated?

I run Ubuntu 9.10, if that has any influence on the answer?

- Jan

---

### Post by patchwork on 2010-03-11
I'm not sure about the panel, but you can create a soft link launcher to the Desktop...

For example, firefox:
```
ln -s /usr/bin/firefox ~/Desktop/firefox.ln
```

---

### Post by jan schoubo on 2010-03-13
Thanks patchwork, that is indeed a very easy way to create a desktop link,
however I want a little more than that, and was hoping for an equaly easy solution :D

I have progressed somewhat farther since my question, but I am still not there.

Below is a script that I use to try this out, that illustrates my findings so far. You apparently use gconftool-2 (or gconf-editor) to manipulate the Gnome configuration.
I have found the relevant parts (/apps/panel/objects/object_nnn and /apps/panel/general/object_id_list), but some questions remain.
I have read some general documentation on gconftool-2 and Gnome Configuration, but found little in the form of examples.

1) I can define the new object and include it in the object_id_list in the .xml file and load it with gconftool-2. The new object and its many keys are included, but the list is not changed. If I then go into gconf-editor and add the new object to the list, VOILA, it immediately appears as I expected. Why can't gconftool-2 do this?

2) How do I delete keys and paths again? (I have created a few extras by now ;)) I have tried various forms like
```

gconftool-2 --direct --config-source xml:readwrite:$HOME/.gconf --recursive-unset /apps/panel/objects/object_17
gconftool-2 --direct --config-source xml:readwrite:$HOME/.gconf --recursive-unset /apps/panel/objects/object_17/*
gconftool-2 --direct --config-source xml:readwrite:$HOME/.gconf --recursive-unset --unset /apps/panel/objects/object_17
gconftool-2 --direct --config-source xml:readwrite:$HOME/.gconf --recursive-unset --unset /apps/panel/objects/object_17/*
# etc...

```
but none seems to make the keys or paths go away? Why?

3) There is also a path /apps/panel/default_setup/objects (and /apps/panel/default_setup/general) - what role do they play? Adding to them seems to make no difference?

4) I have also tried killall gnome-panel or reboot to make the changes appear, but nothing except "by hand" gconf-editor or drag'n'drop seems 
to make visible changes.

Any help will be greatly appreciated.

- Jan

Script so far:
```

#!/bin/bash

echo "
Introduction
============

Create Gnome top panel launcher for a command.

This prototype is not quite working yet, and
simply creates a command that is easy to recognize 
(gedit xxx.xxx).

The script does not change anything on the system, 
unless you hit RETURN when asked (see just before the 
two gconftool-2 calls at the end of the script).

The script creates two files: 
  $HOME/.gnome2/panel2.d/default/launchers/run_gedit.desktop
      This defines the launcher
  ./gconfpart.tmp
      Gnome configuration input XML file 
"

echo "
Define the launcher
===================
"

launchfilename="run_gedit.desktop"
launchfile=$HOME/.gnome2/panel2.d/default/launchers/$launchfilename
cat > $launchfile << [EOD]
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Type=Application
Exec=gedit /home/jschoubo/xxx.xxx
TryExec=
X-GNOME-DocPath=
Terminal=false
Name=Edit xxx.xxx
Name[en_DK]=Ret xxx.xxx
GenericName[en_US]=Edit xxx.xxx
Comment=Very simple example running gedit xxx.xxx
Comment[en_DK]=Meget simpelt eksempel på gedit xxx.xxx
Icon=/usr/share/icons/Humanity/mimes/48/application-zip.svg
[EOD]

echo "
Figure out next available object_n number,
  and rightmost position of existing ones
=========================================
"

# Get list of active objects
objectlist=`gconftool-2 --get /apps/panel/general/object_id_list`


lastn=$(( -1 ))
maxpos=$(( 0 ))
for i in {1..100};
do
  gconftool-2 --dir-exists=/apps/panel/objects/object_$i
  if [ $? -eq 0 ]; then 
    objectwithout=${objectlist/object_$i/FOUND}
    #echo $objectlist
    #echo $objectwithout
    if [ ${objectwithout} != ${objectlist} ]; then
      launcher=`gconftool-2 --get /apps/panel/objects/object_$i/launcher_location`
      lastn=$(( $i )) 
      pos=$(( `gconftool-2 --get /apps/panel/objects/object_$i/position` ))
      echo "    Met object_$i: $launcher at position $pos"
      if [ $pos -gt $maxpos ]; then maxpos=$(( pos )); fi
      # echo "Found position $pos, now maxpos = $maxpos"
    else
      echo "    Met object_$i with no launcher defined"
    fi
  fi
done  
nextn=$(( lastn + 1 ))
nextpos=$(( maxpos + 40 ))
echo "
    Will create launcher as object_$nextn at position $nextpos
"


writeGConfstart() {
  gconfpartfile="gconfpart.tmp"
  echo "<gconfentryfile>
  <entrylist base=\"/apps/panel\">" > $gconfpartfile
}

writeGConfentry() {
  # Parameters:
  # 1: object number
  # 2: key name final part
  # 3: value type
  # 4: value

  echo "    <entry>
      <key>objects/object_$1/$2</key>
      <schema_key>/schemas/apps/panel/objects/$2</schema_key>
      <value>
        <$3>$4</$3>
      </value>
    </entry>" >> $gconfpartfile
}

writeGConflistentry() {
  # Parameters:
  # 1: key name
  # 2: value type
  # 3: value list

  echo "    <entry>
      <key>$1</key>
      <schema_key>/schemas/apps/panel/general/object_id_list</schema_key>
      <value>
        <list type=\"string\">" >> $gconfpartfile

  list=$2
  for i in ${list//,/ };
  do
    echo "          <value>
            <string>$i</string>
          </value>" >> $gconfpartfile
  done

  echo "        </list>
      </value>
    </entry>" >> $gconfpartfile
}

writeGConfend() {
  echo "  </entrylist>
</gconfentryfile>
" >> $gconfpartfile
}


# Add new launcher to active object list
objectlist=${objectlist#[}
objectlist=${objectlist%]}
objectlist=$objectlist,object_$nextn
echo "
    Active objects will be set to:
    {$objectlist} 
"



echo "
Define GConf
============
"
writeGConfstart
writeGConfentry $nextn action_type          string lock
writeGConfentry $nextn attached_toplevel_id string
writeGConfentry $nextn bonobo_iid           string
writeGConfentry $nextn custom_icon          string
writeGConfentry $nextn launcher_location    string $launchfilename
writeGConfentry $nextn locked               bool   false
writeGConfentry $nextn menu_path            string applications:/
writeGConfentry $nextn object_type          string launcher-object
writeGConfentry $nextn panel_right_stick    bool   false
writeGConfentry $nextn position             int    $nextpos
writeGConfentry $nextn tooltip              string
writeGConfentry $nextn toplevel_id          string top_panel_screen0
writeGConfentry $nextn use_custom_icon      bool   false
writeGConfentry $nextn use_menu_path        bool   false
writeGConflistentry general/object_id_list $objectlist
writeGConfend

echo "
Load GConf
==========
"

read -p "Hit RETURN to execute gconftool-2, or CTRL-C to quit " dummy

gconftool-2 --direct --config-source xml:readwrite:$HOME/.gconf --load $gconfpartfile
gconftool-2 --shutdown

read -p "Hit RETURN when you are done " dummy


```

---

### Post by fredyboy10 on 2010-05-04
Any progress on this? I am trying to write a configuration script to be used on many fresh installs that removes the yelp launcher and adds a gnome-terminal.

---

### Post by jan schoubo on 2010-05-04
Sorry, no progress to report, as I have had no time to spend on this recently.

---

### Post by Dart00 on 2010-05-11
I also express great interest in this. Hope you find out how to get this working!

---

