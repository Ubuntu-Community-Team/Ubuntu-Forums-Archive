---
title: "MCE Remote no longer working with 11.10"
date: 2011-10-14
forum: General Help
---

### Post by rico2k_uk on 2011-10-14
I have had ubuntu running for quite a while using xbmc as a front end controlled by my mce remote. I did an upgrade to 11.10 today and now the remote doesnt work at all. It does get detected correctly for every button press in irw but no where else.

Can someone help? I need this sorted fairly quickly as its our mediahub.

---

### Post by nermal0 on 2011-10-15
I've had the same problem after upgrading to oneiric (11.10). Since XBMC did not get an update (it's coming from a separate PPA), I assume the lirc button naming for the "mceusb" driver has changed in the new lirc package. It doesn't match the "mceusb" section in XBMC's /usr/share/xbmc/system/Lircmap.xml anymore.

What I had to do to get my MCE remote working again in XBMC was to create a new file ~/.xbmc/userdata/Lircmap.xml and insert the remote button codes that I gathered from running "irw".

This is mostly the default mapping, with a few customisations for my personal preferences. Note that this is for the "mceusb" driver, if you use a different driver, you have to change the "<remote device="mceusb">" line and gather the correct codes from "irw".

```

<lircmap>
	<remote device="mceusb">
		<left>KEY_LEFT</left>
		<right>KEY_RIGHT</right>
		<up>KEY_UP</up>
		<down>KEY_DOWN</down>
		<select>KEY_OK</select>
		<start>KEY_HOME</start>
		<back>KEY_BACK</back>
		<record>KEY_RECORD</record>
		<play>KEY_PLAY</play>
		<pause>KEY_PAUSE</pause>
		<stop>KEY_STOP</stop>
		<forward>KEY_FORWARD</forward>
		<reverse>KEY_REWIND</reverse>
		<volumeplus>KEY_VOLUMEUP</volumeplus>
		<volumeminus>KEY_VOLUMEDOWN</volumeminus>
		<pageplus>KEY_CHANNELUP</pageplus>
		<pageminus>KEY_CHANNELDOWN</pageminus>
		<skipplus>KEY_NEXT</skipplus>
		<skipminus>KEY_AGAIN</skipminus>
		<subtitle>Teletext</subtitle>
		<mute>KEY_MUTE</mute>
		<power>KEY_POWER</power>
		<myvideo>KEY_VIDEO</myvideo>
		<mymusic>KEY_AUDIO</mymusic>
		<mypictures>Pictures</mypictures>
		<mytv>LiveTV</mytv>
		<one>KEY_1</one>
		<two>KEY_2</two>
		<three>KEY_3</three>
		<four>KEY_4</four>
		<five>KEY_5</five>
		<six>KEY_6</six>
		<seven>KEY_7</seven>
		<eight>KEY_8</eight>
		<nine>KEY_9</nine>
		<zero>KEY_0</zero>
		<red>KEY_RED</red>
		<green>KEY_GREEN</green>
		<yellow>KEY_YELLOW</yellow>
		<blue>KEY_BLUE</blue>
		<select>Aspect</select>
		<info>More</info>
		<title>Guide</title>
		<menu>KEY_DVD</menu>
		<clear>KEY_CLEAR</clear>
		<enter>KEY_ENTER</enter>
	</remote>
</lircmap>

```

---

### Post by whoelse on 2011-10-15
> **nermal0 said:**
> 
What I had to do to get my MCE remote working again in XBMC was to create a new file ~/.xbmc/userdata/Lircmap.xml and insert the remote button codes that I gathered from running "irw".

Thanks. I had the same problem and your solution works great.

---

