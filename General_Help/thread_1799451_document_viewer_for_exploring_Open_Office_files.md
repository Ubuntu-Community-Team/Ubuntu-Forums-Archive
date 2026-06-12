---
title: "document viewer for exploring Open Office files"
date: 2011-07-07
forum: General Help
---

### Post by dragonfly41 on 2011-07-07
I would like to browse quickly through Open Office documents (*.odt etc.) and view content in text without launching documents in Open Office which would just grow the "Recent Documents" list.

There is some discussion on document viewers here .. evince etc.
 [http://brainstorm.ubuntu.com/idea/18068/](http://brainstorm.ubuntu.com/idea/18068/) 


 I have tried file view F3 in Gnome Commander and Tux Commander but there is no Open Office quick viewer plugin (where do we get plugins?).

I've managed to configure windows Total Commander (www,ghisler.com) installed in wine to use this OOView lister plugin

[http://www.totalcmd.net/plugring/OOSimpleViewer.html](http://www.totalcmd.net/plugring/OOSimpleViewer.html)


and I can select any document and F3 allows me to view the document in text form.


Is there a ubuntu native version of Total Commander + plugins   for fast viewing of files which are browsed through quickly?   How to write plugins for GNOME Commander for example?

---

### Post by dragonfly41 on 2011-07-09
I have found Double Commander which looks promising since Total Commander lister plugins (including document viewers) can be added.   e.g. *.wlx plugin.

[http://doublecmd.sourceforge.net/](http://doublecmd.sourceforge.net/)

But I haven't got it to fully work yet in ubuntu 10.10.

I installed doublecmd_0.4.5.1-1gtk2_i386.deb on ubuntu 10.10

When installing the downloaded *.deb through ubuntu software centre I see this warning ..

**[COLOR=Navy]Sorry, 'doublecmd' is not available for this type of computer (i386)[/COLOR]**

but I carried on installing

when I then launch Double Commander from Applications > Accessories

the GUI is not in English.

See the snapshots attached.

Has anyone successfully installed Double Commander?

---

### Post by dragonfly41 on 2011-07-09
I've now learned from Double Commander forum that I can delete the language files and English is the default.  Problem solved.

Plugins need to be compiled for Linux .. not sure yet how to do that.

But Double Commander works by ..

select file
right click (context menu opens)
Open With .. and I use Okular and Xournal

If I get the lister plugins to work I can open from F3.

See instructions here for installing Double Commander on unbuntu 10.10

[FONT=Sans Serif]http://www.webupd8.org/2011/02/download-double-commander-046-deb-works.html[/FONT]



[FONT=Sans Serif]
[/FONT]

---

### Post by dragonfly41 on 2011-07-10
Adding further notes ..

For those looking for a ubuntu alternative to windows Total Commander (other than midnight commander or others) I suggest you look at Double Commander.

[http://doublecmd.sourceforge.net/](http://doublecmd.sourceforge.net/)

Here is a useful guide for installation ..

[http://www.webupd8.org/2011/02/download-double-commander-046-deb-works.html](http://www.webupd8.org/2011/02/download-double-commander-046-deb-works.html)

After trial and error .. for my requirement to view Open Office *.odt files as text I was advised in the DC forum to install odt2txt

sudo apt-get install odt2txt

and then associate *.odt files using this command ..

{!VIEWER} <?odt2txt %p?>

I can now view *.odt files by F3 or context menu.

I would now like to explore how to write plugins.

---

