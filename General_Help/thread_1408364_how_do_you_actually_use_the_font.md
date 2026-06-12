---
title: "how do you actually use the font???"
date: 2010-02-16
forum: General Help
---

### Post by skullsk8er on 2010-02-16
[SIZE=3]hello people, got some time to spare??

so i copied a font called [/SIZE][SIZE=3]AnnabelScript.ttf [/SIZE][SIZE=3]in the /usr/share/fonts/truetype directory 

now I have a html page in which i need to use the font.How the heck:) i can use the characters in this file.

i tried something like 
<div id = "store_header">
            
            <div id = "banner">
                <%= image_tag("logo-top.jpg" ) %>
                <p>
                 Shope<span style="color:black">Books</span>
                </p>
            </div>
.....
</div>
and the css

#banner p{
margin-top:0px;
font-size:60px;
margin-top:30px;
font: "Annabel Script"
}

but doesn't work at all :(

any idea?
[/SIZE]

---

### Post by labinnsw on 2010-02-23
[Please see post Number 5]("http://ubuntuforums.org/showthread.php?t=275202"). In the latest versions of Ubuntu viewing the font also gives the option to install it.

You lost me here.> 
now I have a html page in which i need to use the font

If your font is correctly installed, you use it in HTML the same way you use any other installed font.

---

### Post by Enigmapond on 2010-02-23
Possibly you need to update the font cache. This will update your font folder and also look for .fonts in your home directory to see if there are fonts there to update..

```
sudo fc-cache -f -v
```Any font you find and want to use  doesn't have to be "Installed" just throw them in either one of these folders, run the cache update and you're good to go.

---

