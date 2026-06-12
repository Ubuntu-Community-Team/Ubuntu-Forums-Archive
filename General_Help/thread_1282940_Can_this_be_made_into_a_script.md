---
title: "Can this be made into a script?"
date: 2009-10-05
forum: General Help
---

### Post by ninjapirate89 on 2009-10-05
I found this page which shows how to make Shiretoko look like the real Firefox 3.5 but it takes a long time to input all the commands one after the other. Can it be made into a script?

[http://www.ubuntu-inside.me/2009/07/firefox-35x-branding-fix-for-ubuntu.html]("http://www.ubuntu-inside.me/2009/07/firefox-35x-branding-fix-for-ubuntu.html")

I've already tried this and it does work, but whenever Shiretoko updates it reverts back.

---

### Post by credobyte on 2009-10-05
And why wouldn't it be possible ? Here's a list of all commands ( I suppose they are in the same order as in that guide ): [https://files.getdropbox.com/u/612498/firefox35-branding-commands.txt](https://files.getdropbox.com/u/612498/firefox35-branding-commands.txt) - hunt down the cd commands ( as they will be the main [COLOR=Gray]problem[/COLOR] here ) and you are ready to go :)

---

### Post by c0mput3r_n3rD on 2009-10-05
All a script is is a list of commands....  If you can do it through the prompt you can write into one reusable script.

---

### Post by brettg on 2009-10-05
This is simple

Make a file with a name of your choosing
```

vi script.sh

```
In the very first line of the script put this

```
#!/bin/sh
```

Paste the list of the commands after that and save the file

Make it executable

```
chmod +x script.sh
```

Execute it with;

```
./script.sh
```

---

### Post by ninjapirate89 on 2009-10-05
so it would just be
```

#!/bin/sh
sudo cp -v /usr/lib/firefox-3.0*/icons/* /usr/lib/firefox-3.5*/icons/
cd /usr/lib/firefox-3.5*/defaults/preferences/
sudo cp -v firefox.js_bak firefox.js
sudo cp -v firefox.js firefox.js_bak
sudo sed -i "s/pref(\"general.useragent.extra.firefox\", \"Shiretoko\//pref(\"general.useragent.extra.firefox\", \"Firefox\//g" firefox.js
cd /usr/lib/firefox-3.5*/chrome/
sudo cp browser-branding-en-US.jar_bak browser-branding-en-US.jar
sudo cp browser-branding-en-US.jar browser-branding-en-US.jar_bak
sudo cp browser-branding.jar_bak browser-branding.jar
sudo cp browser-branding.jar browser-branding.jar_bak
cd /usr/lib/firefox-3.0*/chrome/
sudo cp -p browser-branding.jar /usr/lib/firefox-3.5*/chrome/
cd /usr/lib/firefox-3.0*/chrome/icons/default/
sudo cp -p * /usr/lib/firefox-3.5*/chrome/icons/default/
sudo mkdir -p /d2tmp/ffbrandnew/
sudo chmod 755 -R /d2tmp
cd /usr/lib/firefox-3.5*/chrome/
sudo cp browser-branding-en-US.jar /d2tmp/ffbrandnew/
sudo unzip /d2tmp/ffbrandnew/browser-branding-en-US.jar -d /d2tmp/ffbrandnew/
sudo rm -f -r /d2tmp/ffbrandnew/browser-branding-en-US.jar
sudo sed -i "s/<\!ENTITY  brandShortName        \"Shiretoko\">/<\!ENTITY  brandShortName        \"Firefox\">/g" /d2tmp/ffbrandnew/locale/branding/brand.dtd
sudo sed -i "s/<\!ENTITY  brandFullName         \"Shiretoko\">/<\!ENTITY  brandFullName         \"Mozilla Firefox\">/g" /d2tmp/ffbrandnew/locale/branding/brand.dtd
sudo sed -i "s/<\!ENTITY  vendorShortName       \"mozilla.org\">/<\!ENTITY  vendorShortName       \"Mozilla\">/g" /d2tmp/ffbrandnew/locale/branding/brand.dtd
sudo sed -i "s/<\!ENTITY  releaseBaseURL        \"http:\/\/www.mozilla.org\/projects\/shiretoko\/releases\/\">/ /g" /d2tmp/ffbrandnew/locale/branding/brand.dtd
sudo sed -i "s/brandShortName=Shiretoko/brandShortName=Firefox/g" /d2tmp/ffbrandnew/locale/branding/brand.properties
sudo sed -i "s/brandFullName=Shiretoko/brandFullName=Mozilla Firefox/g" /d2tmp/ffbrandnew/locale/branding/brand.properties
sudo sed -i "s/vendorShortName=mozilla.org/vendorShortName=Mozilla/g" /d2tmp/ffbrandnew/locale/branding/brand.properties
cd /d2tmp/ffbrandnew/
sudo zip -r browser-branding-en-US.jar locale
sudo cp /d2tmp/ffbrandnew/browser-branding-en-US.jar /usr/lib/firefox-3.5*/chrome/
cd /usr/bin/
sudo rm -f -r /d2tmp/
sudo rm -f -r firefox
sudo ln -s firefox-3.5 firefox
sudo sed -i "s/Name=Shiretoko Web Browser/Name=Firefox 3.5 Web Browser/g" /usr/share/app-install/desktop/firefox-3.5.desktop
sudo sed -i "s/Comment=Firefox 3.5 Beta/Comment=Browse the World Wide Web/g" /usr/share/app-install/desktop/firefox-3.5.desktop
sudo sed -i "s/GenericName=Preview Browser/GenericName=Web Browser/g" /usr/share/app-install/desktop/firefox-3.5.desktop
sudo sed -i "s/Name=Shiretoko Web Browser/Name=Firefox 3.5 Web Browser/g" /usr/share/applications/firefox-3.5.desktop
sudo sed -i "s/Comment=Firefox 3.5/Comment=Browse the World Wide Web/g" /usr/share/applications/firefox-3.5.desktop
sudo sed -i "s/GenericName=Preview Browser/GenericName=Web Browser/g" /usr/share/applications/firefox-3.5.desktop

```

Edit -> yeah that didn't work. and yes i did make it executable.

---

### Post by brettg on 2009-10-05
Yes. I can't vouch for whether the list of commands is good or not (because I didn't read them) but assuming they work without error at the command line then they should work from such a script.

---

### Post by credobyte on 2009-10-05
> **ninjapirate89 said:**
> so it would just be
Edit -> yeah that didn't work. and yes i did make it executable.

What exactly doesn't work ?

---

### Post by ninjapirate89 on 2009-10-05
This is what I get from running the script as it is written above.
```

`/usr/lib/firefox-3.0.14/icons/document.png' -> `/usr/lib/firefox-3.5.4pre/icons/document.png'
`/usr/lib/firefox-3.0.14/icons/mozicon128.png' -> `/usr/lib/firefox-3.5.4pre/icons/mozicon128.png'
`/usr/lib/firefox-3.0.14/icons/mozicon16.xpm' -> `/usr/lib/firefox-3.5.4pre/icons/mozicon16.xpm'
`/usr/lib/firefox-3.0.14/icons/mozicon50.xpm' -> `/usr/lib/firefox-3.5.4pre/icons/mozicon50.xpm'
`firefox.js_bak' -> `firefox.js'
`firefox.js' -> `firefox.js_bak'
Archive:  /d2tmp/ffbrandnew/browser-branding-en-US.jar
 extracting: /d2tmp/ffbrandnew/locale/branding/brand.dtd  
 extracting: /d2tmp/ffbrandnew/locale/branding/brand.properties  
  adding: locale/ (stored 0%)
  adding: locale/branding/ (stored 0%)
  adding: locale/branding/brand.properties (deflated 30%)
  adding: locale/branding/brand.dtd (deflated 35%)
sed: can't read /usr/share/applications/firefox-3.5.desktop: No such file or directory
sed: can't read /usr/share/applications/firefox-3.5.desktop: No such file or directory
sed: can't read /usr/share/applications/firefox-3.5.desktop: No such file or directory

```

Edit-> And I know it's not the commands themselves because I have done this twice manually inputting one line at a time.

---

### Post by ninjapirate89 on 2009-10-05
> **credobyte said:**
> What exactly doesn't work ?

I wrote the script like this and saved as script.sh then ran chmod +x script.sh
```

#!/bin/sh
sudo cp -v /usr/lib/firefox-3.0*/icons/* /usr/lib/firefox-3.5*/icons/
cd /usr/lib/firefox-3.5*/defaults/preferences/
sudo cp -v firefox.js_bak firefox.js
sudo cp -v firefox.js firefox.js_bak
sudo sed -i "s/pref(\"general.useragent.extra.firefox\", \"Shiretoko\//pref(\"general.useragent.extra.firefox\", \"Firefox\//g" firefox.js
cd /usr/lib/firefox-3.5*/chrome/
sudo cp browser-branding-en-US.jar_bak browser-branding-en-US.jar
sudo cp browser-branding-en-US.jar browser-branding-en-US.jar_bak
sudo cp browser-branding.jar_bak browser-branding.jar
sudo cp browser-branding.jar browser-branding.jar_bak
cd /usr/lib/firefox-3.0*/chrome/
sudo cp -p browser-branding.jar /usr/lib/firefox-3.5*/chrome/
cd /usr/lib/firefox-3.0*/chrome/icons/default/
sudo cp -p * /usr/lib/firefox-3.5*/chrome/icons/default/
sudo mkdir -p /d2tmp/ffbrandnew/
sudo chmod 755 -R /d2tmp
cd /usr/lib/firefox-3.5*/chrome/
sudo cp browser-branding-en-US.jar /d2tmp/ffbrandnew/
sudo unzip /d2tmp/ffbrandnew/browser-branding-en-US.jar -d /d2tmp/ffbrandnew/
sudo rm -f -r /d2tmp/ffbrandnew/browser-branding-en-US.jar
sudo sed -i "s/<\!ENTITY  brandShortName        \"Shiretoko\">/<\!ENTITY  brandShortName        \"Firefox\">/g" /d2tmp/ffbrandnew/locale/branding/brand.dtd
sudo sed -i "s/<\!ENTITY  brandFullName         \"Shiretoko\">/<\!ENTITY  brandFullName         \"Mozilla Firefox\">/g" /d2tmp/ffbrandnew/locale/branding/brand.dtd
sudo sed -i "s/<\!ENTITY  vendorShortName       \"mozilla.org\">/<\!ENTITY  vendorShortName       \"Mozilla\">/g" /d2tmp/ffbrandnew/locale/branding/brand.dtd
sudo sed -i "s/<\!ENTITY  releaseBaseURL        \"http:\/\/www.mozilla.org\/projects\/shiretoko\/releases\/\">/ /g" /d2tmp/ffbrandnew/locale/branding/brand.dtd
sudo sed -i "s/brandShortName=Shiretoko/brandShortName=Firefox/g" /d2tmp/ffbrandnew/locale/branding/brand.properties
sudo sed -i "s/brandFullName=Shiretoko/brandFullName=Mozilla Firefox/g" /d2tmp/ffbrandnew/locale/branding/brand.properties
sudo sed -i "s/vendorShortName=mozilla.org/vendorShortName=Mozilla/g" /d2tmp/ffbrandnew/locale/branding/brand.properties
cd /d2tmp/ffbrandnew/
sudo zip -r browser-branding-en-US.jar locale
sudo cp /d2tmp/ffbrandnew/browser-branding-en-US.jar /usr/lib/firefox-3.5*/chrome/
cd /usr/bin/
sudo rm -f -r /d2tmp/
sudo rm -f -r firefox
sudo ln -s firefox-3.5 firefox
sudo sed -i "s/Name=Shiretoko Web Browser/Name=Firefox 3.5 Web Browser/g" /usr/share/app-install/desktop/firefox-3.5.desktop
sudo sed -i "s/Comment=Firefox 3.5 Beta/Comment=Browse the World Wide Web/g" /usr/share/app-install/desktop/firefox-3.5.desktop
sudo sed -i "s/GenericName=Preview Browser/GenericName=Web Browser/g" /usr/share/app-install/desktop/firefox-3.5.desktop
sudo sed -i "s/Name=Shiretoko Web Browser/Name=Firefox 3.5 Web Browser/g" /usr/share/applications/firefox-3.5.desktop
sudo sed -i "s/Comment=Firefox 3.5/Comment=Browse the World Wide Web/g" /usr/share/applications/firefox-3.5.desktop
sudo sed -i "s/GenericName=Preview Browser/GenericName=Web Browser/g" /usr/share/applications/firefox-3.5.desktop

```

Then ran ./script.sh and was given this:
```

`/usr/lib/firefox-3.0.14/icons/document.png' -> `/usr/lib/firefox-3.5.4pre/icons/document.png'
`/usr/lib/firefox-3.0.14/icons/mozicon128.png' -> `/usr/lib/firefox-3.5.4pre/icons/mozicon128.png'
`/usr/lib/firefox-3.0.14/icons/mozicon16.xpm' -> `/usr/lib/firefox-3.5.4pre/icons/mozicon16.xpm'
`/usr/lib/firefox-3.0.14/icons/mozicon50.xpm' -> `/usr/lib/firefox-3.5.4pre/icons/mozicon50.xpm'
`firefox.js_bak' -> `firefox.js'
`firefox.js' -> `firefox.js_bak'
Archive:  /d2tmp/ffbrandnew/browser-branding-en-US.jar
 extracting: /d2tmp/ffbrandnew/locale/branding/brand.dtd  
 extracting: /d2tmp/ffbrandnew/locale/branding/brand.properties  
  adding: locale/ (stored 0%)
  adding: locale/branding/ (stored 0%)
  adding: locale/branding/brand.properties (deflated 30%)
  adding: locale/branding/brand.dtd (deflated 35%)
sed: can't read /usr/share/applications/firefox-3.5.desktop: No such file or directory
sed: can't read /usr/share/applications/firefox-3.5.desktop: No such file or directory
sed: can't read /usr/share/applications/firefox-3.5.desktop: No such file or directory

```

---

### Post by brettg on 2009-10-05
The clue is this;

 "can't read /usr/share/applications/firefox-3.5.desktop"

If you do ```
ls /usr/share/applications/firefox-3.5.desktop
```

does it produce an error?

---

