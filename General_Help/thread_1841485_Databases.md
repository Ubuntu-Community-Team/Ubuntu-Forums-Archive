---
title: "Databases"
date: 2011-09-09
forum: General Help
---

### Post by jonathonblake on 2011-09-09
I'm trying to slash phone costs.( The definition used by my dictionary, and the definition used by the phone company are mutually exclusive definitions.)
I can download phone records for each line in CSV format.

What I'd like to do, is click on one or two buttons, and have the following automatically displayed:
* The longest conversations;
* the most frequently called numbers;
* the phone numbers that have the most billed time;

With that information, I can toss the five or so top numbers in each category into a pool that the phone company theoretically won't bill me for calling.  

Are there are any currently available tools that run on Linux that provide that functionality, or do I need to roll my own?

jonathon

---

### Post by haqking on 2011-09-09
> **jonathonblake said:**
> I'm trying to slash phone costs.( The definition used by my dictionary, and the definition used by the phone company are mutually exclusive definitions.)
I can download phone records for each line in CSV format.

What I'd like to do, is click on one or two buttons, and have the following automatically displayed:
* The longest conversations;
* the most frequently called numbers;
* the phone numbers that have the most billed time;

With that information, I can toss the five or so top numbers in each category into a pool that the phone company theoretically won't bill me for calling.  

Are there are any currently available tools that run on Linux that provide that functionality, or do I need to roll my own?

jonathon


import into a spreadhseet and then some simple formulas i imagine.

Depends on the data i guess.

---

### Post by jonathonblake on 2011-09-09
> **haqking said:**
> import into a spreadhseet and then some simple formulas i imagine.


I'm currently using a spreadsheet, but that is sub-optimal from a dozen different perspectives, the most significant being that spreadsheets have a tendency to destroy data, without providing any indication that that has happened.

jonathon

---

### Post by haqking on 2011-09-09
> **jonathonblake said:**
> I'm currently using a spreadsheet, but that is sub-optimal from a dozen different perspectives, the most significant being that spreadsheets have a tendency to destroy data, without providing any indication that that has happened.

jonathon


Do they ? I would be more inclined to say the user does that.

In what respect ?

What sort of formulas are you currenlty using that is doing this ?

Spreadhsheets must not be used by anyone then...LOL ;-)

---

### Post by jonathonblake on 2011-09-09
> **haqking said:**
> Do they ? I would be more inclined to say the user does that.

The human error is in thinking that spreadsheets do not silently destroy data.

Depending upon the spreadsheet that is used, and the locale it is set to, 09/01/2011 is silently converted to either 1 September 2011, 9 January 2011, 11 January 2009, or 20 January 2009. The first is an unobvious error, whilst the latter two are obvious errors.

00000000086 gets truncated to 86.

With some spreadsheets, 999-9999 gets replaced by -9000, and 404-834-1066 gets replaced by -1496.

Those are just some of the errors I've seen happen, doing nothing more than importing the csv.

jonathon

---

