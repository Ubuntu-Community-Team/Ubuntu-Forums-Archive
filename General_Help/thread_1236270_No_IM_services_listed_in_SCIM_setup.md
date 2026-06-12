---
title: "No IM services listed in SCIM setup"
date: 2009-08-10
forum: General Help
---

### Post by DarkerStar on 2009-08-10
Hi there,

A year or so ago I enabled Japanese text input on my en_CA Feisty system with Anthy and SCIM. Since then I've upgraded (several times) to Jaunty, and everything is still working fine, &#12391;&#12375;&#12423;&#12358;. But now I need to add a new input method... and the only options in SCIM are the ones I've already activated.

When I go to System -> Preferences -> SCIM Input Method Setup, the program opens normally and I see my settings. But in IMEngine -> Global Setup, I only see:
[list][*]Japanese
[list][*]Anthy[/list]
[*]Other
[list][*]English/European
[*]RAW CODE[/list][/list]That's it - nothing else, not even disabled. All of those options are selected, but there should be dozens and dozens more that are not selected (even just for en_CA, and I have *at least* ja, fr_FR, pl and eo installed also).

Where are all the other options gone?

-----------------------------------------

And a maybe related question: when I installed Japanese input way back when, I had to use a combination of SCIM and XIM to get Japanese input to work in all my applications (especially Qt ones). I believe SCIM has matured since then. Perhaps if I completely reinstalled SCIM, making sure that all the old XIM stuff is eliminated, it might fix the problem above? But does SCIM work everywhere now? Even in Qt apps? (Or should I wait for Karmic Koala?)

---

### Post by Irihapeti on 2009-08-10
You need to install some additional packages: scim-m17n contains a whole lot of options and there's a scim-canna package for Japanese as well. Scim-tables-ja also contains some Japanese options, but I gather from the documentation that they are rather primitive.

Please note, I know almost nothing about Japanese input; I only use Simplified Chinese.

If scim-bridge-client-qt and scim-bridge-client-qt4 are installed (probably are by default), then you can use scim in qt apps as well.

I've found I can use scim in java apps if I add my locale to the first line of /etc/scim/global, like this:

```
/SupportedUnicodeLocales = en_US.UTF-8,en_NZ.UTF-8
```

Note that there is no space after the comma.

If your locale is en_US.UTF-8, then you don't need to edit the file.

I'm using Hardy, but I think that the Jaunty configuration is pretty much the same.

---

### Post by DarkerStar on 2009-08-10
l10n, i18n and now m17n. ^_^; That's a new one for me.

Thank you very much, worked like a charm!

---

### Post by Irihapeti on 2009-08-10
You're welcome. Glad to know it worked.

---

