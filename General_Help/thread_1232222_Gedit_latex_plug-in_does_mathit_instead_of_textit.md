---
title: "Gedit latex plug-in does mathit instead of textit"
date: 2009-08-05
forum: General Help
---

### Post by masil on 2009-08-05
Hi all,

I've encountered this weird problem with the Gedit Latex Plug-in. Seemingly out of the thin air, upon clicking the italics button in the Gedit latex plug-in toolbar to italicize text, the command that gets inserted automatically is no longer textit but mathit.

This switch happened for no apparent reason as I was working on a document that I've been working on for a few weeks now without encountering this problem before.

The switch has only occurred with regard to this one document. Other documents that I edit continue to work normally.

Does anyone have an idea what is going on? Did I unbeknownst to me manage to change a setting?

Many thanks.
Masil

---

### Post by eeg on 2009-09-10
Hi, got here via a google search. Had the same problem as you (even tho
I'm using Archlinux).

Don't know for sure what causes it, but you can override this behaviour
by modifying this file :

/usr/lib/gedit-2/plugins/LaTeXPlugin/toolbar/LaTeXToolbar.py
(the location might be different in Ubuntu)

Change all "mathit" instances to "textit". Restart gedit and it should
work as before.


```

class FontStyleMenu (FormatMenu):
	def __init__(self, instance):
		FormatMenu.__init__(self, instance)
		items = [
			("bf", _("Bold"), {TEXT : ["\\textbf{", "}"], MATH : ["\\textbf{", "}"]}, "\\textbf | \\mathbf"),
			("it", _("Italic"), {TEXT : ["\\textit{", "}"], MATH : ["\\textit{", "}"]}, "\\textit | \\mathit"),
			("underline", _("Underline"), ["\\underline{", "}"], "\\underline"),
			("sc", _("Small Capitals"), {TEXT : ["\\textsc{", "}"]}, "\\textsc"),
			None,

```


HTH,
eeg

---

### Post by hawthornso23 on 2009-09-10
Basic question but - are you possibly in math mode? If you typed a $ sign this will switch you into math mode. If the plugin was designed by someone with some intelligence I would expect the function of the italic button to switch to mathitalic when in math mode.

---

