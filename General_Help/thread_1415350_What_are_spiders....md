---
title: "What are spiders...???"
date: 2010-02-24
forum: General Help
---

### Post by robertcoulson on 2010-02-24
See attachment...Just wondering what spiders are...???
Robert

---

### Post by robertcoulson on 2010-02-24
Yikes..here is attachment

---

### Post by Barrucadu on 2010-02-24
Programs which crawl (and usually index) webpages&#8212;eg, googlebot.

---

### Post by Ozymandias_117 on 2010-02-24
Rofl, that's wierd

---

### Post by robertcoulson on 2010-02-24
Thanks...very much.
Robert

---

### Post by wojox on 2010-02-24
Spiders are essentially programs that “crawl” sites and report back to their superior (Google or whatever search engine they were created for) what their findings are. Their purpose is to make it easy for sites to get listed in search engines.

---

### Post by lisati on 2010-02-24
They are "visitors" from search engines, looking for nuggets of information to show people when they do a search with web sites like Google or Yahoo.

Have a look here: [http://en.wikipedia.org/wiki/Web_crawler](http://en.wikipedia.org/wiki/Web_crawler)

Edit: I like wojox's turn of phrase "report back to their superior", posted while I was typing. :)

---

### Post by robertcoulson on 2010-02-24
Oh..I see..It said Members, Guests and Spiders.....Thought for a minute there was a 3rd living organism that I was not aware of....Ha,ha.
Robert

---

### Post by Dayofswords on 2010-02-24
There is.

---

### Post by robertcoulson on 2010-02-24
So, does that mean there are some outside programs watching the Ubuntu forum and what they are using to search and what we search...???
Robert

---

### Post by JackRock on 2010-02-24
> **robertcoulson said:**
> So, does that mean there are some outside programs watching the Ubuntu forum and what they are using to search and what we search...???
Robert

They're simply looking at the forum and its content, so the pages can come up on search engines' results pages.

---

### Post by robertcoulson on 2010-02-24
Hey Jackrock..Are these out side spiders or Ubuntu spiders...???
Rovert

---

### Post by uRock on 2010-02-24
They belong to different sites like Google, Yahoo, and Bing. That is why when you do a google search for a Ubuntu problem it usually links you to UF.

---

### Post by robertcoulson on 2010-02-24
Big brother watching...???
Robert

---

### Post by robertcoulson on 2010-02-24
P.S. Is that legal...???
Robert

---

### Post by Barrucadu on 2010-02-25
> **robertcoulson said:**
> P.S. Is that legal...???
Robert

It better be, or otherwise every search engine is breaking the law :p

---

### Post by lotharmat on 2010-02-25
Websites can specify in a robots.txt file what can and cannot be indexed.

Take UF for example

```
User-agent: *
Crawl-delay: 20
```

Microsoft.com's
```

# Robots.txt file for http://www.microsoft.com
#

User-agent: *
Disallow: /*/mac/help.mspx
Disallow: /*/mac/help.mspx?
Disallow: /*/mactopia/help.mspx?
Disallow: /australia/mac/help.mspx?
Disallow: /belux/fr/mac/help.mspx?
Disallow: /blacklisted*
Disallow: /brasil/mac/help.mspx?
Disallow: /businesssolutions/community/newsgroups/
Disallow: /Businesssolutions/Community/Newsgroups/
Disallow: /canada/Library/mnp/2/aspx/
Disallow: /communities/bin.aspx
Disallow: /communities/blogs/PortalResults.mspx
Disallow: /communities/eventdetails.mspx
Disallow: /communities/rss.aspx
Disallow: /danmark/mac/help.mspx?
Disallow: /downloads/*/results.aspx?
Disallow: /downloads/Browse.aspx
Disallow: /downloads/browse.aspx
Disallow: /downloads/info.aspx
Disallow: /downloads/thankyou.aspx
Disallow: /events/advsearch.mspx?*
Disallow: /finland/mac/help.mspx?
Disallow: /france/formation/centres/planning.asp
Disallow: /france/ie/default.asp
Disallow: /france/mac/help.mspx?
Disallow: /france/mnp_utility.mspx
Disallow: /genuine/ajax/
Disallow: /genuine/common/
Disallow: /genuine/Content.aspx
Disallow: /genuine/csr/
Disallow: /genuine/diag/Error.aspx
Disallow: /genuine/diag/error.aspx
Disallow: /genuine/diag/Instructions.aspx
Disallow: /genuine/diag/instructions.aspx
Disallow: /genuine/diag/RunDiags.aspx
Disallow: /genuine/diag/rundiags.aspx
Disallow: /genuine/diag/Support.aspx
Disallow: /genuine/diag/support.aspx
Disallow: /genuine/downloads/AutomaticUpdates.aspx
Disallow: /genuine/downloads/Default.aspx
Disallow: /genuine/downloads/default.aspx
Disallow: /genuine/downloads/Error.aspx
Disallow: /genuine/downloads/error.aspx
Disallow: /genuine/downloads/GenerateHTA.aspx
Disallow: /genuine/downloads/LicenseStoreError.aspx
Disallow: /genuine/downloads/nongenuine.aspx
Disallow: /genuine/downloads/nongenuineVista.aspx
Disallow: /genuine/downloads/PluginInstructions.aspx
Disallow: /genuine/downloads/RunHTA.aspx
Disallow: /genuine/downloads/SuccessfulActivation.aspx
Disallow: /genuine/downloads/TryAgain.aspx
Disallow: /genuine/downloads/Validate.aspx
Disallow: /genuine/downloads/VAMTPrivacyInfo.aspx
Disallow: /genuine/downloads/VistaDisclosure.aspx
Disallow: /genuine/downloads/VLKInstructions.aspx
Disallow: /genuine/hip/
Disallow: /genuine/IPtoGeoMap/
Disallow: /genuine/notify/
Disallow: /genuine/oe/
Disallow: /genuine/offers/Details.aspx
Disallow: /genuine/offers/details.aspx
Disallow: /genuine/office/BrowserAlternative.aspx
Disallow: /genuine/office/CounterfeitReport.aspx
Disallow: /genuine/office/FailureReport.aspx
Disallow: /genuine/office/nongenuine.aspx
Disallow: /genuine/office/OfficeKeyUpdate.aspx
Disallow: /genuine/office/OfficeKeyUpdateCheck.aspx
Disallow: /genuine/office/OfficeKeyUpdateResults.aspx
Disallow: /genuine/office/OfficeNongenuine.aspx
Disallow: /genuine/office/PluginInstructions.aspx
Disallow: /genuine/office/PrintableCounterfeitReport.aspx
Disallow: /genuine/office/PurchaseError.aspx
Disallow: /genuine/office/PurchaseInfoReport.aspx
Disallow: /genuine/office/ReportInstructions.aspx
Disallow: /genuine/office/ResultsReport.aspx
Disallow: /genuine/office/SuccessfulValidation.aspx
Disallow: /genuine/office/Validate.aspx
Disallow: /genuine/purchase/
Disallow: /genuine/rd.aspx
Disallow: /genuine/selfhelp/Error.aspx
Disallow: /genuine/selfhelp/PkuInstructions.aspx
Disallow: /genuine/selfhelp/PostKitPurchase.aspx
Disallow: /genuine/selfhelp/ValidatePID.aspx
Disallow: /genuine/selfhelp/ValidationHelp.aspx
Disallow: /genuine/selfhelp/ValidationHelpResults.aspx
Disallow: /genuine/selfhelp/ViewExample.aspx
Disallow: /genuine/survey/
Disallow: /genuine/test/
Disallow: /genuine/validate/default.aspx
Disallow: /genuine/vista/AEDetail.aspx
Disallow: /genuine/vista/AERepair.aspx
Disallow: /genuine/vista/CounterfeitReport.aspx
Disallow: /genuine/vista/LocationByRegion.aspx
Disallow: /genuine/vista/PrintableCounterfeitReport.aspx
Disallow: /genuine/vista/PurchaseError.aspx
Disallow: /genuine/vista/PurchaseInfoReport.aspx
Disallow: /genuine/vista/ReportInstructions.aspx
Disallow: /genuine/vista/VistaLegalization.aspx
Disallow: /genuine/windows7/
Disallow: /genuine/wizard/
Disallow: /Germany/kleinunternehmen/euga/detail.mspx
Disallow: /Germany/kleinunternehmen/euga/results.mspx
Disallow: /germany/library/images/mnp/
Disallow: /germany/mac/help.mspx?
Disallow: /germany/mnp_utility.mspx
Disallow: /germany/video/de/de/related
Disallow: /hk/mac/help.mspx?
Disallow: /hpc/en/us/supported-applications.aspx?SortField*
Disallow: /ie/ie40/
Disallow: /info/customerror.htm
Disallow: /info/smart404.asp
Disallow: /intlkb/
Disallow: /ireland/mac/help.mspx?
Disallow: /isapi/
Disallow: /italy/products/mac
Disallow: /italy/products/mac/help.mspx?
Disallow: /Japan/DirectX/default.asp
Disallow: /japan/directx/default.asp
Disallow: /japan/enable/textview.asp
Disallow: /japan/mactopia/help.mspx
Disallow: /japan/mnp_utility.mspx
Disallow: /japan/products/library/search.asp
Disallow: /japan/showcase/print/default.aspx
Disallow: /japan/terminology/query.asp
Disallow: /latam/mac/help.mspx?
Disallow: /library/gallery/components/ratingcontrol/ratings.aspx?rurl*
Disallow: /library/toolbar/3.0/
Disallow: /mac/help.mspx
Disallow: /mnp_utility.mspx
Disallow: /netherlands/mac/help.mspx?
Disallow: /netherlands/mnp_utility.mspx
Disallow: /norge/mac/help.mspx?
Disallow: /nz/mac/help.mspx?
Disallow: /resources/casestudies/casestudyimageshow.asp
Disallow: /resources/casestudies/CompanyLogoShow.asp
Disallow: /resources/casestudies/ddi/companylogoshow.asp
Disallow: /resources/casestudies/ddi/showfile.asp
Disallow: /resources/casestudies/FindCaseStudyResults.aspx
Disallow: /resources/casestudies/showfile.asp
Disallow: /security_essentials/market.aspx?
Disallow: /singapore/mac/help.mspx?
Disallow: /spain/empresas/
Disallow: /spain/mac/help.mspx?
Disallow: /spain/medianaempresa/
Disallow: /sverige/mac/help.mspx?
Disallow: /uk/mac/help.mspx?
Disallow: /uk/mnp_utility.mspx
Disallow: /video/en/us/related
Disallow: /windows/compatibility/windows-vista/Browse.aspx
Disallow: /windows/compatibility/windows-vista/Details.aspx
Disallow: /windows/compatibility/windows-vista/browse.aspx
Disallow: /windows/compatibility/windows-vista/details.aspx
Disallow: /windowsmobile/catalog/
Disallow: /windowsmobile/components/referafriend/getcallbackresult.aspx

Sitemap: http://www.microsoft.com/bi/sitemap.xml
Sitemap: http://www.microsoft.com/business/smb/sitemapindex.xml
Sitemap: http://www.microsoft.com/business/success/sitemap.xml
Sitemap: http://www.microsoft.com/canada/sitemap.xml
Sitemap: http://www.microsoft.com/downloads/sitemap.aspx
Sitemap: http://www.microsoft.com/dynamics/sitemap.xml
Sitemap: http://www.microsoft.com/ebs/sitemap.xml
Sitemap: http://www.microsoft.com/en/ca/sitemap.xml
Sitemap: http://www.microsoft.com/everybodysbusiness/sitemap.xml
Sitemap: http://www.microsoft.com/fr/ca/sitemap.xml
Sitemap: http://www.microsoft.com/germany/kleinunternehmen/gsitemap.aspx
Sitemap: http://www.microsoft.com/infrastructure/sitemap.xml
Sitemap: http://www.microsoft.com/msft/reports/sitemap.xml
Sitemap: http://www.microsoft.com/online/sitemap.xml
Sitemap: http://www.microsoft.com/sbs/sitemap.xml
Sitemap: http://www.microsoft.com/security_essentials/sitemap.xml
Sitemap: http://www.microsoft.com/sitemapindex.xml
Sitemap: http://www.microsoft.com/unlimitedpotential/sitemap.xml
Sitemap: http://www.microsoft.com/unlimitedpotential/video-sitemap.xml
Sitemap: http://www.microsoft.com/windows/sitemap.xml
Sitemap: http://www.microsoft.com/windowsazure/sitemap.xml
Sitemap: http://www.microsoft.com/windowsmobile/en-us/sitemap.xml

```

---

### Post by Dr Droid on 2010-02-25
Spiders are like robots that aid search engines in finding data. Yes there are probably some spiders crawling in these forums as well.  I'm not sure how to prevent such a tool. I think that's part of the reason ubuntuforums put the questions in the search function like 1+2 = ? so that only humans can get access to the forum preventing spam and the like... Not sure, this is just a little bit of my understanding

---

### Post by robertcoulson on 2010-02-25
Interesting...Glad you explained it a bit more..Thanks.
Robert

---

### Post by uRock on 2010-02-26
You can check this out too. If you want. [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1252380](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1252380)

---

### Post by robertcoulson on 2010-02-26
Thanks iRock..I went to the link and read some more about it...Thanks.
Robert

---

