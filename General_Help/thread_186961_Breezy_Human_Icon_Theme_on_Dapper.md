---
title: "Breezy Human Icon Theme on Dapper?"
date: 2006-06-02
forum: General Help
---

### Post by Footissimo on 2006-06-02
Hiya!

Not a big fan of the Dapper human icon theme, particularly as my Desktop is rather blue-ish :)  The old human theme on Breezy was great though...I don't suppose anyone knows where I can find it?  Tried the repos and no luck..even though the legacyhuman theme is available for everything **but** the icons :( :(

Thanks in advance

Edit:  If I remember right, the Breezy human theme used the GNOME icons, though the human icons (the ones I'm looking for) were a choice..

---

### Post by Rui Pais on 2006-06-02
hi,
well there is a Blue Human, maybe it fits you:
[http://www.gnome-look.org/content/show.php?content=37099]("http://www.gnome-look.org/content/show.php?content=37099")
[http://www.gnome-look.org/content/show.php?content=36396]("http://www.gnome-look.org/content/show.php?content=36396")

or you can try a search here at [Art Gnome]("http://art.gnome.org/themes/icon/").

edit, another suggestion, 
download a ubuntu-artwork.deb from here:
[http://archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-artwork/]("http://archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-artwork/")
one of the all (that maus be there all ubuntu versions...) maybe ubuntu-artwork_0.2.14.2-1_all.deb, open with your archive manager and inside data.tar.gz there is a folder /usr/share/icons/human :)

hth

---

### Post by temcat on 2006-06-02
Try Etiquette icon theme (don't remember if it exists in repositories, but you can always download it from gnome-look.org). It is fairly complete, unintrusive (unlike the default Dapper theme!) and goes well in a blueish setup.

---

### Post by cleentrax on 2006-06-02
The Breezy icons are included with Dapper. They're called "LegacyHuman."

---

### Post by Footissimo on 2006-06-03
[QUOTE=Rui Pais]hi,
well there is a Blue Human, maybe it fits you:
[http://www.gnome-look.org/content/show.php?content=37099]("http://www.gnome-look.org/content/show.php?content=37099")
[http://www.gnome-look.org/content/show.php?content=36396]("http://www.gnome-look.org/content/show.php?content=36396")

or you can try a search here at [Art Gnome]("http://art.gnome.org/themes/icon/").

edit, another suggestion, 
download a ubuntu-artwork.deb from here:
[http://archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-artwork/]("http://archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-artwork/")
one of the all (that maus be there all ubuntu versions...) maybe ubuntu-artwork_0.2.14.2-1_all.deb, open with your archive manager and inside data.tar.gz there is a folder /usr/share/icons/human :)

hth[/QUOTE]

Thanks for this - the one 0.2.27 seems to be the Breezy human icon set - tried seeing if the deb would work (after deinstalling 28 - the dapper human icon set) but I had a few red-x's ...then tried to dump the contents of 0.2.27 into /usr/share/icons/Human/ etc but the old set was SVGs whilst the dapper set is based on pngs...so the theme instructions seem to point to them and ignore the Breezy ones...grr!  Even my sledgehammer approach didn't work :(  I'll have a look at the icon theme instructions and see if I can work out how it works 


[QUOTE=cleentrax]The Breezy icons are included with Dapper. They're called "LegacyHuman."[/QUOTE]

The 'Control' and 'Border' have a legacyhuman theme, but not the icon themes - see screenie below :( :(

[http://img75.imageshack.us/img75/2593/screenshot9ur.png](http://img75.imageshack.us/img75/2593/screenshot9ur.png)

---

### Post by Rui Pais on 2006-06-03
Hi again,

problems happen if you mix Human icon sets (or mixed same name icon sets) specially if one is svg and other png based...

Try to clean ubuntu-artwork (uninstall, purge, delete /usr/share/icons/human folder, reinstall ubuntu-artwork).

Then, open 0.2.27 with file-roller, open data.tar.gz inside and copy folder /usr/share/icons/human to /usr/share/icons/ but **with other name**, like HumanBreezy, OldHuman what ever. 
Edit index.theme file inside and rename Name=Human to Name=HumanBreezy (or the one you choose).
(*EDIT:* you can change the line Inherits=... to Inherits=Tango,Human,gnome too. That way if an icon don't exist it will look on other icon themes)

Then you can simply choose it from 'icons' on Theme selector.

hth.

---

### Post by Footissimo on 2006-06-03
I love you.

It worked :)  Dapper now looks Dapper.  I'll write a HOWTO later as it has been asked on other threads.

Thankyou.

---

### Post by Rui Pais on 2006-06-03
[QUOTE=Footissimo]I love you.[/QUOTE]
Sorry i would never trust anyone with a cat like your? his smiles looks suspicious to me ;)

:)
Joking. Glad to help.

have fun

---

