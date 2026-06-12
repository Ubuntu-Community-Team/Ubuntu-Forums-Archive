---
title: "Gdesklets and stickynotes"
date: 2006-01-25
forum: General Help
---

### Post by cbudden on 2006-01-25
Hello.

I am having a problem with stickynotes.  When I log on or restart the desklet, this error comes up. :
[IMG]http://static.flickr.com/23/91177610_104e7c802b_o.png[/IMG]

I click ignore and I don't get the error for the rest of my session.  Next session the error comes up again.  

This is the /usr/share/gdesklets/Displays/stickynotes/notes.display file:

```
<?xml version="1.0" encoding="UTF-8"?>
<display window-flags="sticky, below">
	<meta author="Jack Gallagher"
		category="Misc/Utilities"
		dependancy="gdesklets cvs"
		description="Sticky notes on your desktop"
		name="StickyNotes"
		preview="gfx/preview.png"
		version="0.1" />
	
	<image x="0" y="0" uri="gfx/note.png" />
	<label id="note1" x="20" y="10" value="" font="Sans bold 10"/>
	<label id="note2" x="20" y="30" value="" font="Sans bold 10"/>
	<label id="note3" x="20" y="50" value="" font="Sans bold 10"/>
	<label id="note4" x="20" y="70" value="" font="Sans bold 10"/>
	<label id="note5" x="20" y="90" value="" font="Sans bold 10"/>
	<label id="note6" x="20" y="110" value="" font="Sans bold 10"/>
	<label id="note7" x="20" y="130" value="" font="Sans bold 10"/>
	<label id="note8" x="20" y="150" value="" font="Sans bold 10"/>
	<prefs callback="prefs_cb">
		<page label="Note">
			<string label="1st line:" bind="Dsp.note1.value" help="What the note will say"/>
			<string label="2nd line:" bind="Dsp.note2.value" help="What the note will say"/>
			<string label="3rd line:" bind="Dsp.note3.value" help="What the note will say"/>
			<string label="4th line:" bind="Dsp.note4.value" help="What the note will say"/>
			<string label="5th line:" bind="Dsp.note5.value" help="What the note will say"/>
			<string label="6th line:" bind="Dsp.note6.value" help="What the note will say"/>
			<string label="7th line:" bind="Dsp.note7.value" help="What the note will say"/>
			<string label="8th line:" bind="Dsp.note8.value" help="What the note will say"/>
		</page> 
	</prefs>
</display>

```

How can I fix this?

Thanks

---

### Post by rippon on 2006-01-25
Your not alone. Same thing happens with the sticky notes and a few other Gdesklets.

---

### Post by cbudden on 2006-01-25
Ah, so probably no fix then.

---

### Post by dysfunctional on 2006-12-21
same problem here... still no solution?

---

### Post by hizaguchi on 2007-03-06
Old thread, but in case anybody is still getting this error, I just edited the notes.display file and removed "callback="prefs_cb"" the <prefs> tag.  Works fine now.

---

