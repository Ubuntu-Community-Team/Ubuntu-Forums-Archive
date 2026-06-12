---
title: "i need the download link for the latest STABLE java plugin"
date: 2009-07-22
forum: General Help
---

### Post by eival on 2009-07-22
i had been having issues with javascripts recently an it wasnt till now going through the Mozilla add-ons that i realise i have 

1.6.0_14-b08  currrently installed, the "b" im assuming means Beta, which would clearly be the culprit for lockups/freezes.

only problem is i went to java.com an its telling me i have the recommended version already installed.

i tried looking at the older versions but that page is way too confusing with the million drop down boxes.

i just want the last stable release if anyone knows please post the download link, thanks.

---

### Post by michy99 on 2009-07-22
The version in the repository is 1.6.0_14.

---

### Post by QIII on 2009-07-22
You have the most recent Update. 

I believe "b" is for build.

Here's my version

```
java version "1.6.0_14"
Java(TM) SE Runtime Environment (build 1.6.0_14-b08)
Java HotSpot(TM) 64-Bit Server VM (build 14.0-b16, mixed mode)
```

If you have any doubts:

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-bin sun-java6-fonts sun-java6-jdk
```

To make sure that Sun's Java is the priority if OpenJDK is installed:    

```
sudo update-java-alternatives -s java-6-sun
```

```
java -version
```

---

### Post by running_rabbit07 on 2009-07-22
I am running this one in the screenshot that is installed via Synaptic. Not sure it will be your fix but why not try?

Of coarse I read the Jumper"s post after typing mine and seeing he has the CLI install of that same plug-in.

---

### Post by eival on 2009-07-23
i ran the terminal codes above but im still having freeze issues when JS is needed in a page, im using the latest ubuntu update of Firefox too, 3.12.

does anyone know what else could be causing the issue?

---

### Post by eival on 2009-07-25
okay Java now loads up properly with no issues, i guess yesterday's update fixed it

---

