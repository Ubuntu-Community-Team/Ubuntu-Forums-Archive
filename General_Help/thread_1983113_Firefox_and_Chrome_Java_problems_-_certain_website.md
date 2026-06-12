---
title: "Firefox and Chrome Java problems - certain websites"
date: 2012-05-19
forum: General Help
---

### Post by aoniumo on 2012-05-19
Why don't Java load properly in certain websites:

*Hpshopping
*Morningstar.com
*Newegg.com
*Laptopmagazine.com

In hpshopping, I cannot click on "Customize" button to customize a laptop.  I have to keep reloading the page until I can.

The same at morningstar.com, newegg.com, laptopmagazine.  There are  tabs, for example, at morningstar.com if you are viewing a mutual funds  portfolio holdings: Equity View and Equity Prices - but they don't load  properly.

At laptopmagazine.com, when looking at reviews, certain things don't load.

This has always been the case since I started using 11.04 version, but  I'm getting sick of keeping to reload pages or opening multiple pages of  the same site until I get lucky and a page loads correctly.

---

### Post by strask on 2012-05-19
Can you please provide a more exact URL to a page that you have a problem with? I can't even find a website named hpshopping, for example. Just cut and paste the complete address from your browser.

---

### Post by aoniumo on 2012-05-19
Screenshots of hpshopping, morningstar, and laptopmagazine and circled in red are the sections of the website that don't load properly or links where I'm unable to click.




Websites like amazon.com, facebook, twitters, linkedin, reuters, google, gmail are ok.

---

### Post by aoniumo on 2012-05-19
URLS:

portfolios.morningstar.com/fund/holdings?t=RERGX
[http://portfolios.morningstar.com/fund/holdings?t=MLAIX&region=USA&culture=en-US](http://portfolios.morningstar.com/fund/holdings?t=MLAIX&region=USA&culture=en-US)
[http://performance.morningstar.com/fund/performance-return.action?t=TRRNX&region=USA&culture=en-US](http://performance.morningstar.com/fund/performance-return.action?t=TRRNX&region=USA&culture=en-US)
[http://portfolios.morningstar.com/fund/holdings?t=TRRNX&region=USA&culture=en-us](http://portfolios.morningstar.com/fund/holdings?t=TRRNX&region=USA&culture=en-us)
[http://performance.morningstar.com/fund/performance-return.action?t=MLAIX&region=USA&culture=en-us](http://performance.morningstar.com/fund/performance-return.action?t=MLAIX&region=USA&culture=en-us)
[http://performance.morningstar.com/fund/performance-return.action?t=RERGX&region=USA&culture=en-us](http://performance.morningstar.com/fund/performance-return.action?t=RERGX&region=USA&culture=en-us)
Others at morningstar.com

[http://www.laptopmag.com/review/laptops/samsung-series-7-gamer.aspx](http://www.laptopmag.com/review/laptops/samsung-series-7-gamer.aspx)
[http://www.laptopmag.com/review/laptops/eurocomm-monster.aspx](http://www.laptopmag.com/review/laptops/eurocomm-monster.aspx)
[http://www.laptopmag.com/review/laptops/origin-eon-17s.aspx](http://www.laptopmag.com/review/laptops/origin-eon-17s.aspx)
[http://www.laptopmag.com/review/laptop/asus-g75vw-ds71.aspx](http://www.laptopmag.com/review/laptop/asus-g75vw-ds71.aspx)
[http://www.laptopmag.com/review/laptops/toshiba-qosmio-x775-3dv78.aspx](http://www.laptopmag.com/review/laptops/toshiba-qosmio-x775-3dv78.aspx)
[http://www.laptopmag.com/review/laptops/asus-g74sx-a2.aspx](http://www.laptopmag.com/review/laptops/asus-g74sx-a2.aspx)
All other at [www.laptopmag.com](www.laptopmag.com)

[http://www.shopping.hp.com/](http://www.shopping.hp.com/)
[http://www.shopping.hp.com/en_US/home-office/-/static/page-envy](http://www.shopping.hp.com/en_US/home-office/-/static/page-envy)
[http://www.shopping.hp.com/en_US/home-office/-/products/Laptops/Laptops](http://www.shopping.hp.com/en_US/home-office/-/products/Laptops/Laptops)
eTc, etc.

---

### Post by aoniumo on 2012-05-20
Also bon-ton.com's site doesn't load properly.  Cannot click on links

---

### Post by 0011235813 on 2012-05-20
You have an issue with Java or *JavaScript*? I'm a bit confused here! If JavaScript is the issue, in Chrome go to Preference- Settings- Content Settings- JavaScript: Tick "Allow Pages to Execute JavaScript (recommended)". In FF, go to edit- preferences- content- allow JavaScript to run.

If Java is the issue, have you installed something Iced Tea or OpenJDK? These can cause issues in certain sites that are programmed for the proprietary Java (install that from Oracle's site).

PS: I have no issue with any of those sites, so it's got nothing to do with Ubuntu.

---

### Post by aoniumo on 2012-05-20
> **0011235813 said:**
> You have an issue with Java or *JavaScript*? I'm a bit confused here! If JavaScript is the issue, in Chrome go to Preference- Settings- Content Settings- JavaScript: Tick "Allow Pages to Execute JavaScript (recommended)". In FF, go to edit- preferences- content- allow JavaScript to run.

If Java is the issue, have you installed something Iced Tea or OpenJDK? These can cause issues in certain sites that are programmed for the proprietary Java (install that from Oracle's site).

PS: I have no issue with any of those sites, so it's got nothing to do with Ubuntu.

Those settings are already enabled in both browsers.
I only have issues with certain sites.  My sister has a Windows 7 platform and she has issues with firefox and chrome as well with pages not loading properly or links not being clickable, AND she does not have iced tea or Openjdk.

I didn't say linux is the problem.

I checked and I don't have Iced Tea or OpenJDK installed.

---

### Post by strask on 2012-05-20
> **aoniumo said:**
> Those settings are already enabled in both browsers.

I get exactly the problems your screenshots show if I turn javascript off. If your browser has javascript enabled, maybe you have some sort of firewall or proxy that is blocking javascript functionality?

---

### Post by 0011235813 on 2012-05-20
> **strask said:**
> I get exactly the problems your screenshots show if I turn javascript off. If your browser has javascript enabled, maybe you have some sort of firewall or proxy that is blocking javascript functionality?
+1

> **aoniumo said:**
> Those settings are already enabled in both browsers.
I only have issues with certain sites.  My sister has a Windows 7 platform and she has issues with firefox and chrome as well with pages not loading properly or links not being clickable, AND she does not have iced tea or Openjdk.

I didn't say linux is the problem.

I checked and I don't have Iced Tea or OpenJDK installed.

Well I think JavaScript is the problem here, damn these marketing names. Those things aren't normally associated with Java, so I'll discount that. 

By the way, if you DO need the Java plugin for anything, you WILL have to install either Iced Tea, OpenJDK or Oracle Java.

I would follow the above posters advice and check you don't have something blocking JS on your network.

---

