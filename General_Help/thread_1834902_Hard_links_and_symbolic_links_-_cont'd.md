---
title: "Hard links and symbolic links - cont'd"
date: 2011-08-28
forum: General Help
---

### Post by Paddy Landau on 2011-08-28
I know [this]("http://ubuntuforums.org/showthread.php?t=1242445") is an old thread.

There are **three** types of links that I understand. All  types have their advantages, and I use them all according to my needs.
[LIST=1]
[*]Hard link
[*]Absolute symbolic link (references the absolute path of the source file)
[*]Relative symbolic link (references the relative path of the source file)
[/LIST]
As an example, consider the following commands.
```
mkdir --parents ~/parent/sub      [COLOR=DarkRed]*# Create a subdirectory ~/parent/sub.*[/COLOR]
cd ~/parent/sub                   [COLOR=DarkRed]*# Go to the subdirectory.*[/COLOR]
touch ../orig                     [COLOR=DarkRed]*# Create a file orig in the parent.*[/COLOR]
ln ../orig hard                   [COLOR=DarkRed]*# Hard link: orig <--> sub/hard*[/COLOR]
ln -s ../orig relative            [COLOR=DarkRed]*# Relative symbolic link: sub/relative -> orig*[/COLOR]
ln -s ~/parent/orig absolute      [COLOR=DarkRed]*# Absolute symbolic link: sub/relative -> orig*[/COLOR]

[COLOR=DarkRed]* # Look at the results.*[/COLOR]
ls -l --color
[B]total 20
lrwxrwxrwx 1 paddy paddy 23 2011-08-28 13:18 [/B][B][COLOR=DeepSkyBlue]absolute[/COLOR] -> /home/paddy/parent/orig
-rw-r--r-- 2 paddy paddy  0 2011-08-28 13:18 [COLOR=Blue]hard[/COLOR]
lrwxrwxrwx 1 paddy paddy  7 2011-08-28 13:18 [COLOR=DeepSkyBlue]relative[/COLOR] -> ../orig[/B]
```Note the difference between the the absolute and relative links.

Here are some tests.

[LIST]
[*]Move *parent* (along with *sub*). The hard and relative links will persist (even if to a different mount point); the absolute link will fail.
[*]Move *sub*, leaving *parent* alone, keeping within the same mount point. The hard and absolute links will persist; the relative link will fail.
[*]Move *sub*, leaving *parent* alone, to a different mount point. The hard link will be severed, becoming instead a copy of *orig*; the absolute link will persist; the relative link will fail.
[/LIST]
Therefore, you need to choose the type of link according to your needs. As you already implied, backups are an important consideration.

---

### Post by Iowan on 2011-08-28
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may [COLOR="Blue"]link to the original discussion in the new thread if you think it may be helpful.[/COLOR]
:)

---

### Post by Paddy Landau on 2011-08-28
Iowan, thanks for the advice and moving my post. (BTW, you put the wrong link, so I've corrected it.)

However, there is a disadvantage in doing that; the OP won't know about my reply. Under these specific circumstances, wouldn't it better for the OP to know?

---

