---
title: "How to get sound working on HDTV"
date: 2011-06-04
forum: General Help
---

### Post by steigerjb on 2011-06-04
I have System76's Leopard Extreme connected to a Samsung t22a350 hdtv/computer monitor with an hdmi. [http://www.newegg.com/Product/Product.aspx?Item=N82E16824001503 ]("http://www.newegg.com/Product/Product.aspx?Item=N82E16824001503") I can't for the life of me get sound to work with the monitor's built in speakers.  Do you know what I need to do?

---

### Post by Joe- on 2011-06-04
System>Preferences>Sound
And change the output to the HDMI connector?

---

### Post by steigerjb on 2011-06-04
> **Joe- said:**
> System>Preferences>Sound
And change the output to the HDMI connector?

I don't think so. 

[IMG]http://i51.tinypic.com/osucr7.png[/IMG]

---

### Post by wolfgar on 2011-06-04
I have a Samsung SyncMaster XL2370HD, but use external computer speakers.

However, To hook up PC audio, it should be a standard 3.5mm male to 3.5mm male connection.

In some cases, it may be a RCA to 3.5mm I'd definitely recommend taking a look to see which connection in the back of the television denotes "PC" when associated with audio. 

You can download the Samsung T22A350 HDTV-Monitor - Manual from here:
[http://static.highspeedbackbone.net/pdf/Samsung%20T22A350%20HDTV-Monitor%20-%20Manual.pdf](http://static.highspeedbackbone.net/pdf/Samsung%20T22A350%20HDTV-Monitor%20-%20Manual.pdf)

I hope this helps...

---

### Post by Hedgehog1 on 2011-06-04
These are my steps for audio over hdmi: 

[**_Natty How To: Audio over HDMI for NVidia_**]("http://ubuntuforums.org/showthread.php?t=1741294")

***The Hedge***

:KS

---

### Post by steigerjb on 2011-06-04
> **Hedgehog1 said:**
> These are my steps for audio over hdmi: 

[**_Natty How To: Audio over HDMI for NVidia_**]("http://ubuntuforums.org/showthread.php?t=1741294")

***The Hedge***

:KS

No luck

---

### Post by Joe- on 2011-06-04
What about the 'output' tab on the sound preferences? Are there any options to change the output?

---

### Post by steigerjb on 2011-06-04
> **Joe- said:**
> What about the 'output' tab on the sound preferences? Are there any options to change the output?

I changed that to hdmi too.  I am at a loss here.

---

### Post by Joe- on 2011-06-04
Like wolfgar said try a 3.5 audio cable (green ones I think?) ?

---

### Post by steigerjb on 2011-06-04
> **Joe- said:**
> Like wolfgar said try a 3.5 audio cable (green ones I think?) ?

audio cables?

---

### Post by Joe- on 2011-06-04
One of these: 


Just use that for the sound.

---

### Post by steigerjb on 2011-06-04
> **Joe- said:**
> One of these: 


Just use that for the sound.

Where do they plug to?  I can't find where it would.

System 76 Leopard Extreme
Samsung t22a350

---

### Post by paalfe on 2011-06-04
You probably have a muted IEC958 channel in alsamixer.
Run alsamixer in terminal and unmute IEC958 (digital) channel(s).

---

### Post by steigerjb on 2011-06-04
> **paalfe said:**
> You probably have a muted IEC958 channel in alsamixer.
Run alsamixer in terminal and unmute IEC958 (digital) channel(s).

Its not an alas issue.  Windows 7 on the same computer has no sound.  Says hdmi not connected.

It is so I don't know what the issue is.

DVI -> HDMI adapter not allowed?

---

### Post by Joe- on 2011-06-05
DVI doesn't carry audio, is your screen a TV or a computer monitor, because my PC monitor has a connector in the back that allows you to connect and standard 3.5Mm audio cable ?

---

### Post by Rebelli0us on 2011-06-05
Are u running as root? Sound is disabled in the root account.

---

### Post by steigerjb on 2012-03-27
> **Joe- said:**
> DVI doesn't carry audio, is your screen a TV or a computer monitor, because my PC monitor has a connector in the back that allows you to connect and standard 3.5Mm audio cable ?

Yeah, my TV manual says using a DVI to HDMI won't carry audio.

---

