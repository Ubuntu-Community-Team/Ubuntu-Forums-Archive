---
title: "How to use unicode or special characters in Gedit Snippets?"
date: 2011-12-07
forum: General Help
---

### Post by davidvaz on 2011-12-07
Hi,

I'm creating some snipplets but there's a problem with some characters.

For example:

If you create a "dollar" to "$", it will work!

If you create a "euro" to "£", it will [COLOR=Red]NOT work[/COLOR]!
If you create a "theta" to "&#952;", it will [COLOR=Red]NOT work[/COLOR]!

Not work is: the word changes to a TAB.

What can I do to insert any characters? Is that possible?

David

---

### Post by lechien73 on 2011-12-07
Hi & welcome to the forums :)

Hmmmm...that is an interesting one.

Ok, I've never used the snippets plug-in, so I installed it and got exactly the same results as you. I found, though, that all of my snippets were lost when I quit from Gedit.

I think this was to do with permissions on the xml file, though, so:

```
sudo chmod 666 /usr/share/gedit/plugins/snippets/global.xml
```

did the trick. The special characters problem remained, however.

On my Ubuntu 11.10 installation, the local copy of the global.xml file is stored in ~/.config/gedit/snippets. It gets corrupted when you try to add a snippet that contains a special character using the manager.

My solution was to add the special characters by editing the global.xml file. The trick is that if you edit it using Gedit, then you get issues because it already has the file open in the background, so:

```
nano ~/.config/gedit/snippets/global.xml
```

Add the special characters, as in my example below, and save the file. It will then work for you. It must be a bug in the snippets manager, because it continues to work when you add new non-special character snippets using the manager afterwards.

Example:

```
<?xml version='1.0' encoding='utf-8'?>
<snippets>
  <snippet>
    <description>New snippet</description>
  </snippet>
  <snippet>
    <text><![CDATA[&#8364;]]></text>
    <tag>euro</tag>
    <description>euro</description>
  </snippet>
  <snippet>
    <text><![CDATA[&#952;]]></text>
    <tag>theta</tag>
    <description>theta</description>
  </snippet>
</snippets>

```

---

