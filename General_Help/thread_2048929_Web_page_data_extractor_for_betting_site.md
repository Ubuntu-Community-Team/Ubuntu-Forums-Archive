---
title: "Web page data extractor for betting site"
date: 2012-08-27
forum: General Help
---

### Post by GSD4ME on 2012-08-27
Dear all

My interest is betting and I would like to save myself a lot of time extracting useful information from a website ([www.Coral.co.uk](www.Coral.co.uk)) - specifically the coupons for "weekend football" (Left hand side - "Football Coupons" > "Weekend Coupons")
Trawling through the data for all the leagues (English, Scottish, French, Italian etc. etc) is time consuming and I would like to be able to automate the process

I have been doing a Google search on things like Data Extractors/Miners etc but don't know:
- Are they suitable for 'drilling' down web site data links that I am not sure of how they are organised on the site? Examining the page source shows that the data itself is only displayed when a link is pressed
- How easy are they to use? 
- Exporting to (eg a spreadsheet) - they seem to be able to do so but are they compatible with Open Office?
- anything else that could help me do what I would like to?

The data would only be extracted once a week so doesn't have to run continuously, simply set it off and watch it do what I would like.

Has anyone got any experience or comments as to the use of these packages and a recommendation as to what is the easiest/most efficient one to use?

Many thanks

---

### Post by CrusaderAD on 2012-08-27
I've never found one worth using. If anyone does, please let us know. What I suggest you can try is automating a

```
wget
```

command for this page and download the source regularly. Have it emailed to yourself (or stored on your hard drive) and view it whenever you want. You could scrub the source code to extract whatever you're looking for, but that would take some more programming.

---

