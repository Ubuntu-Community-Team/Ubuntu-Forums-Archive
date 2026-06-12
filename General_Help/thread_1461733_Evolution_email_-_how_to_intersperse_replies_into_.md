---
title: "Evolution email - how to intersperse replies into quoted email?"
date: 2010-04-24
forum: General Help
---

### Post by AndyHardy on 2010-04-24
Hi,

I use 'quoted' style for reply emails.

I want to be able to intersperse my replies within a quoted reply i.e. if the email had three paragraphs, I'd like to be able to have my replies between each of the paragraphs.

At the moment, I don't seem to be able to do anything other than delete from the quoted section - I try to simulate my requirements by cutting and then 'paste quotation', but this doesn't always work as sometimes Evolution adds too many levels of '> ' .

Any ideas?

---

### Post by dcstar on 2010-04-25
> **AndyHardy said:**
> Hi,

I use 'quoted' style for reply emails.

I want to be able to intersperse my replies within a quoted reply i.e. if the email had three paragraphs, I'd like to be able to have my replies between each of the paragraphs.

At the moment, I don't seem to be able to do anything other than delete from the quoted section - I try to simulate my requirements by cutting and then 'paste quotation', but this doesn't always work as sometimes Evolution adds too many levels of '> ' .


Works perfectly on my system - as it has in every Evolution version I have used in the last 5 years.

Are you using HTML?

---

### Post by AndyHardy on 2010-04-25
> **dcstar said:**
> Works perfectly on my system - as it has in every Evolution version I have used in the last 5 years.

Are you using HTML?

I have everything set to plain text, the replies are shown with '> ' rather than HTML lines and the editing mode is 'Plain Text'.

I've just done some test replies and notice that the behaviour is not consistent - some emails allow me to break them for replies and others don't... for example one from an Outlook Express user is fine, another from a YahooClassic user isn't. Maybe it's because the contained a reply and the former didn't? Looks like I need to experiment.

Thanks for your help,

---

### Post by dcstar on 2010-04-25
> **AndyHardy said:**
> I have everything set to plain text, the replies are shown with '> ' rather than HTML lines and the editing mode is 'Plain Text'.

I've just done some test replies and notice that the behaviour is not consistent - some emails allow me to break them for replies and others don't... for example one from an Outlook Express user is fine, another from a YahooClassic user isn't. Maybe it's because the contained a reply and the former didn't? Looks like I need to experiment.

Thanks for your help,

If you are sent messages in non-standard formats (like HTML) then you may experience this issue.

Try editing the reply in HTML format if it behaves unusually.

---

### Post by FlyboyFred on 2010-11-24
Sorry to resurrect an old thread, but I'm having this same problem. It doesn't matter if I'm in plain text or HTML, I can't break the quoted text to insert a reply. I've tried selected text and changing the indent, but it doesn't help. Any ideas?

I think this bug report might be related: [https://bugs.launchpad.net/ubuntu/+source/gtkhtml3.14/+bug/288185](https://bugs.launchpad.net/ubuntu/+source/gtkhtml3.14/+bug/288185)

---

### Post by AndyHardy on 2010-11-25
> **FlyboyFred said:**
> Sorry to resurrect an old thread, but I'm having this same problem. It doesn't matter if I'm in plain text or HTML, I can't break the quoted text to insert a reply. I've tried selected text and changing the indent, but it doesn't help. Any ideas?

I think this bug report might be related: [https://bugs.launchpad.net/ubuntu/+source/gtkhtml3.14/+bug/288185](https://bugs.launchpad.net/ubuntu/+source/gtkhtml3.14/+bug/288185)

Yup, that's the problem. It doesn't look there is any intention on fixing it...

---

