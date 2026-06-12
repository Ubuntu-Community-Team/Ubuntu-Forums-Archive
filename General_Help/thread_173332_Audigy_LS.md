---
title: "Audigy LS"
date: 2006-05-10
forum: General Help
---

### Post by grip82 on 2006-05-10
Hi all,

I've got some strange problems with my audigy LS card. I followed the install guide on the ALSA [page](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+LS.&chip=SB0310%2C+P17&module=ca0106)  and got sound working a couple of weeks ago. 

However, now all I hear is noise when I try to play sound, and all quiet when I turn the sound off.

Here is some date you might need to know:

```

cat /proc/asound/cards

0 [CA0106         ]: CA0106 - CA0106
                     AudigyLS [Unknown] at 0xa000 irq 16
1 [UART           ]: MPU-401 UART - MPU-401 UART
                     MPU-401 UART at 0x330, irq 10

```

```

sudo lspci | grep -i audio

0000:05:06.0 Multimedia audio controller: Creative Labs SB Audigy LS

```

```

cat .asoundrc

pcm.ca0106 {
        type hw
    card 0
}

ctl.ca0106 {
        type hw
        card 1
}

```

When I open up my volume control in gnome, every sound port appears double, however, when I open alsamixer in console it doesn't. 

When I go to Preferences -> Sound, the sound server is enabled, but I can't select a default sound card. The listbox is grayed out, and nothing is selected. 

Can anyone please help me? I'd be so grateful, since this is my last real problem before switching to ubuntu completely. Thanks all !!

---

