---
title: "curl -K command outputs weird symbols instead of downloading URL from file"
date: 2011-05-16
forum: General Help
---

### Post by meridionaljet on 2011-05-16
Hello,

I'm on Ubuntu 11.04. I have read around about how to use curl to download a list of URLs from a text file, and everyone says to use ```
curl -K URLlist.txt
```. This is what the curl man page says as well. However, for even a simple file with one URL, this command outputs a bunch of weird symbols for me instead of downloading the file.

For example, I have a text file "test.txt" with one line in the following format:

```
url = "http://www.example.com/image.jpg"
```

I use the curl command to download this file:

```
curl -K test.txt
```

...and get something similar to the following output for a long time before the command finally exits:

```
&#65533;&#65533;`s:O&#65533;&#65533;n&#65533;*n&#65533;9 t&#65533;&#65533;jI|y&#65533;&#65533;yt{H&#65533;m5;	9/u&#65533;&#1196;&#65533;&#65533;W&#65533;&#65533;&#65533;.&#65533;`&#65533;D&#65533;#&#65533;T&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#825;&#65533;&#65533;'&#65533;_&#65533;r&#65533;&#65533;&#19963;&#65533;6&#65533;&#65533;;==&#1125;&#65533;&#65533;_&#65533;&#65533;Y&#65533;&#65533;k&#65533;;	c&#65533;v&#65533;&#65533;Y&#65533;&#65533;&#65533;e&#65533;&#65533;pax&#65533;&#65533;w&#65533;?#-+&#65533;&#65533;w&#65533;&#65533;;+&#65533;&#65533;&#65533;S&#65533;&#65533;&#65533;=|&#65533;&#65533;	g&#65533;%&#65533;w&#1583;&#65533;&#65533;Q&#65533;&#65533;V&#65533;&#65533;D&#65533;gY{#q&#65533;&#65533;.vF&#65533;dX&#65533;`*,&#65533;&#65533;<&#65533;_R&#65533;&#65533;&#65533;m&#65533;&#65533;z-&#65533;z&#65533;&#65533;&#65533;g$&#65533;d&#65533;&#65533;&#65533;&#65533;W&#65533;&#65533;&#65533;&#65533;~&#1848;&#65533;&#65533;_&#65533;&#65533;&#65533;&#65533;&#31693;h&#65533;&#65533;O&#65533;
```

No downloaded file shows up after the command is complete. I have no idea why the curl command is not working correctly here. Any help would be appreciated.

---

### Post by mr clark25 on 2011-05-16
curl is working as it should. you just need to either declare an output file, or output it to a file using the ">" character.

example:
```

curl -k list.txt > image.jpg

```

that will make a file called "image.jpg" in you current working directory.

the reason it does that is that an image does not use text encoding, which is what curl outputs.

---

### Post by meridionaljet on 2011-05-16
> **mr clark25 said:**
> curl is working as it should. you just need to either declare an output file, or output it to a file using the ">" character.

example:
```

curl -k list.txt > image.jpg

```

that will make a file called "image.jpg" in you current working directory.

the reason it does that is that an image does not use text encoding, which is what curl outputs.

Thanks a lot. This solves the problem.

---

