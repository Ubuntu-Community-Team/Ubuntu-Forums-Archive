---
title: "Thunderbird Date and Time format"
date: 2010-10-18
forum: General Help
---

### Post by mosaic2s on 2010-10-18
Using ubuntu 10.04 with thunderbird 3.0.8.

The date format is -
Sunday 17 October 2010 10:16pm.
Whereas this can be many formats. Is there a way to select  format of the date and time for use in thunderbird?

Or if this can be shortened to
Sun 17Oct10 10:16pm

---

### Post by njsharp on 2010-10-27
I hope this is of some use to you and others.  I dare say we are all a bit unimpressed by the lack of tools in Thunderbird to allow format choices.  Here's a perhaps somewhat messy approach for you to consider, at your own risk!

My short date preference is for yyyy-mm-dd, whereas my locale en_AU.UTF8 causes dd/mm/yy, so what I have just done is
   sudo gedit
   /usr/share/i18n/locales/en_AU
and change the short format date line (d_fmt) to this:
   d_fmt       "<U0025><U0059><U002D><U0025><U006D><U002D><U0025><U0064>"
which just has to be a unicode character version of:
   %Y-%m-%d
and delivers eg 2010-10-27

The time format line is:
   t_fmt       "<U0025><U0054>"
which equates to %T, which is fine by me.  It delivers eg 15:33:45

These formats are from the date command, see:
   man date

Then I did:
   sudo locale-gen en_AU.UTF8
Generating locales...
  en_AU.UTF-8... done
Generation complete.
and was pleased on restarting Thunderbird to find today's mail now marked eg
   2010-10-27 15:33

Yes, changing the locale will affect anything else which uses it, but that's OK for me, I hope!

Hope this helps.  If it wrecks, remember, it was your risk.

I'm not sure where locale-gen comes from, but it is probably in the locales package installable with the synaptic package manager.

Oh, and yes, you might find yourself having to redo this after an update or reinstall.

---

