---
title: "Problems with wget"
date: 2010-04-28
forum: General Help
---

### Post by Blackie_lawless666 on 2010-04-28
Hi everybody, 
 
I tried to use wget to download a page as shown below 
 
wget --cookies=on --keep-session-cookies --save-cookies=cookie.txt [https://evisaforms.state.gov/default.asp?PostCode=ALG+++++++&CountryCode=ALGR++++++&CountryCodeShow=&PostCodeShow=&Submit=Submit](https://evisaforms.state.gov/default.asp?PostCode=ALG+++++++&CountryCode=ALGR++++++&CountryCodeShow=&PostCodeShow=&Submit=Submit)
 
wget --referer=https://evisaforms.state.gov/default.asp?PostCode=ALG+++++++&CountryCode=ALGR++++++&CountryCodeShow=&PostCodeShow=&Submit=Submit --cookies=on --load-cookies=cookie.txt --keep-session-cookies --save-cookies=cookie.txt [https://evisaforms.state.gov/make_calendar.asp?nDate=5/1/2010&nbarcode=f1T11w30o](https://evisaforms.state.gov/make_calendar.asp?nDate=5/1/2010&nbarcode=f1T11w30o) 
 
As soon as I run the second line the terminal closes itself, any idea? I using Ubuntu 9.10.

---

