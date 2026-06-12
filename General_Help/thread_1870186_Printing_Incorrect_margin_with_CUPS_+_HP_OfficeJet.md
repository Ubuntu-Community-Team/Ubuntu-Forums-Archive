---
title: "Printing: Incorrect margin with CUPS + HP OfficeJet 8500 Wireless"
date: 2011-10-26
forum: General Help
---

### Post by medicdave on 2011-10-26
Hi All-

I'm trying to print address labels with the following setup:

[LIST]
[*]HP OfficeJet Pro 8500 Wireless
[*]Ubuntu Linux 10.04
[*]HP Linux Imaging and Printing System 3.10.2
[*]OpenOffice.org 3.2.0 build 9483
[/LIST]

All prints are offset down by 3/32"; the printer or driver is apparently introducing a minimum top margin. This is tolerable for normal printing, but wrecks havoc when trying to print labels.

I have verified the page settings in OpenOffice.org, confirmed that the printer is configured for US-Letter paper, and checked for margin settings in the Printer Administration "Properties" dialog. I confirmed the offset by creating a blank OpenOffice.org word processing document, setting the margins to 1 inch on all sides, and creating a frame that fills 100% of the text area with no margins. When printed, the Left and Right margins are correct, but the entire frame (exactly 9" high) is translated down by 3/32".

I believe I've isolated the issue to the print driver; I exported the frame test document to a PDF file and printed it with evince. It measured symmetric on-screen, but the same 3/32" vertical offset was still present in the printed version.

Is there anything I can do to correct these margins? I am thinking about trying the latest version of the HP software, but a) there's nothing in the [changelog]("http://hplipopensource.com/hplip-web/release_notes.html") addressing margin issues since 3.10.2, and b) I don't want to break what's (mostly) working now.

Thanks,
Dave

---

