---
title: "Setting up http://localhost/&lt;docpath&gt; in Bluefish editor."
date: 2012-02-05
forum: General Help
---

### Post by dragonfly41 on 2012-02-05
In Bluefish editor I can't get apache hosted php files to launch as http://localhost/<docpath>

e.g. my apache htdocs are placed here .. /home/username/public_html/ .. 

not in the usual apache location /var/www/

If I launch manually in firefox .. [http://localhost/phpinfo.php](http://localhost/phpinfo.php)
I can see the php running in apache as expected.

But if I try launching  same file from Bluefish editor .. "view in browser" .. I can't launch [http://localhost/](http://localhost/) etc in firefox url.

I know that localhost path needs to be setup in preferences (I've done this in other editors).

The "external commands" in Bluefish preferences needs a command which launches the Bluefish file in firefox 

the default firefox command which comes with Bluefish is
> 
firefox -remote 'openURL(%p)' || firefox '%p'&


But this does not map to localhost.  I searched and read this old thread ..

[http://ubuntuforums.org/showthread.php?t=1034844](http://ubuntuforums.org/showthread.php?t=1034844)

and tried to add a new command "Firefox localhost"
pasting in this string in command field ..

> 
firefox -new-window `echo "http://localhost/%s" | sed s/"home\/username\/public_html\/"/""/`


But for some reason Bluefish does not allow this command line to be pasted in as an added browser command.

Any clues as to setting up local host in Bluefish?  Is the above command syntax correct?

---

### Post by dragonfly41 on 2012-02-06
I've tried setting up Bluefish URI mapping to [http://localhost](http://localhost) but with no success.
I'm sure there must be a way in Bluefish but I don't want to mess around using browser SED commands.
So I've decided to install and try Komodo-Edit-7.0.0-p615-linux-x86

Here are the instructions I found for installing he free editor .. (but download the later version of **Edit** 7.0 and don't download the **IDE** at this page which is a 21 day trial of a try before buy product).

[http://usefulubuntu.blogspot.com/2011/03/install-komodo-edit-6-on-natty.html](http://usefulubuntu.blogspot.com/2011/03/install-komodo-edit-6-on-natty.html)

One useful feature in Komodo is an internal preview window so when previewing localhost content I don't have to keep switching back to firefox (or other browser)  .. although that option is also there for different browser paths.

Bluefish does seem to be rich in other features.   I just wish it could be easier for setting up URI mapping and previewing localhost content in situ.

---

