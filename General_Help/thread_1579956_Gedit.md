---
title: "Gedit"
date: 2010-09-22
forum: General Help
---

### Post by oscargodson on 2010-09-22
I was wondering how in Gedit to get it to have normal pastes. When I paste a block of code now it either indents the first line or removes indents on the first line, but the lines below are either fine or not matched with the first line... 

Example starting code:
```

<footer>
	<h3>Terms</h3>
	<p>NET 30 Days. Finance Charge of 0.25% will be made on unpaid balances after 30 days.</p>
			
	<p>Electronic payments can be made via PayPal to the email address above. Mailed checks will be considered late if the postmark date is after the due date above.</p>
</footer>

``` 

and I ended up pasting code below it, the code below it could end up looking like (even tho the tabs are correct and everything before pasting):
```
 
<footer>
	<h3>Terms</h3>
	<p>NET 30 Days. Finance Charge of 0.25% will be made on unpaid balances after 30 days.</p>
			
	<p>Electronic payments can be made via PayPal to the email address above. Mailed checks will be considered late if the postmark date is after the due date above.</p>
</footer>
		<address>
	1234 NW 123rd Ave,<br>
	Portland, OR, 12345<br>
	oscargodson@somecoolsite.com<br>
	(xxx) xxx-xxx<br>
   </address>

```

And remember, all languages and markup do this. HTML, JS, CSS, PHP, text, etc. If you know how to fix or a plugin to fix this, let me know!

---

### Post by 3Miro on 2010-09-22
Where are you pasting from? Is it another file opened with Gedit or some other program. Basically, the tabs on the pasted text are fine, except for the first and last line. If the other text comes from a browser and/or windows document and/or another program, there might be "hidden" characters that show in Gedit as space.

---

### Post by oscargodson on 2010-09-22
> **3Miro said:**
> Where are you pasting from? Is it another file opened with Gedit or some other program. Basically, the tabs on the pasted text are fine, except for the first and last line. If the other text comes from a browser and/or windows document and/or another program, there might be "hidden" characters that show in Gedit as space.

No, its in Gedit still. I can literally copy a block of code and duplicate it below and it wont match.

---

### Post by 3Miro on 2010-09-22
> **oscargodson said:**
> No, its in Gedit still. I can literally copy a block of code and duplicate it below and it wont match.

I just tried it on my Gedit and it works fine. I am not using Ubuntu right now, so I will test it later today again, but this doesn't seem to be general issue with Gedit. Have you tried enabling/disabling automatic indentation and are you running any special plugins? Maybe you have a buggy plugin.

---

### Post by oscargodson on 2010-09-22
> **3Miro said:**
> I just tried it on my Gedit and it works fine. I am not using Ubuntu right now, so I will test it later today again, but this doesn't seem to be general issue with Gedit. Have you tried enabling/disabling automatic indentation and are you running any special plugins? Maybe you have a buggy plugin.

Hmm, not sure. I mean, to recreate this, you could use very basic HTML page, and then place the two HTML elements i have above. Copy the <address> or <footer> tag and try to paste above and/or below.

I have auto-indent on, but I just tried without and it just does it a different way. Instead it makes the first line all the way at the left edge instead of a bad guess like auto-indent.

And also I turned off my plugins like "auto tab" and "modelines" and still acts the same and i remember it acting like this forever. I've just finally decided to ask. For example, doing the exact same set of steps, TextMate does it right, but Gedit will move the first or last line in the totally wrong position, or, the first and last line will be right, but all the inner code is off.

---

### Post by 3Miro on 2010-09-22
I don't know what to tell you. I tested this on Ubuntu 10.04, fully updated. No problems. I made two .html files and was able to copy and paste between them without any loss of indentation. The only time that I can remember having trouble with indentation in Gedit was with windows formated files, but for Gedit to Gedit, it works fine for me.

Sorry I couldn't help.

---

