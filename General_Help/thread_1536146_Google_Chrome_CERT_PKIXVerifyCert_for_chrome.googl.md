---
title: "Google Chrome CERT_PKIXVerifyCert for chrome.google.com"
date: 2010-07-21
forum: General Help
---

### Post by pearj on 2010-07-21
When I try to visit certain https sites, specifically: [https://chrome.google.com/extensions?hl=en-US](https://chrome.google.com/extensions?hl=en-US)
Google Chrome just sits there doing nothing.  If I open up the same url in Firefox it loads up normally.

If I start google-chrome from a terminal window there is an error when I close google chrome after visiting the above url:

[28827:28842:52384805096:ERROR:net/base/x509_certificate_nss.cc(651)] CERT_PKIXVerifyCert for chrome.google.com failed err=-8180
zsh: segmentation fault  google-chrome

I am running Ubuntu 10.04 lucid 64 bit and I am running google chrome version 5.0.375.99.
However to be sure I tried google-chrome-unstable 5.0.360.5-r42969 (I repackaged it from an older machine) and 6.0.466.0-r52279
I also tried chromium 6.0.473.0~svn20100721r53140-0ubuntu1~ucd1~lucid and 5.0.342.9~r43360-0ubuntu2

All exhibited the same behaviour which seems to suggest some sort of underlying library issue.

Another person in my Office Running Fedora 13 has the same problem as well as 2 others running Ubuntu 9.10 Karmic

Strangely enough my old machine running 9.04 Jaunty works ok with the most recent google-chrome-stable, but running from the command line produced some interesting messages:

(pkix_CacheCert_Add: PKIX_PL_HashTable_Add for Certs skipped: entry existed
(pkix_CacheCert_Add: PKIX_PL_HashTable_Add for Certs skipped: entry existed
[27331:27412:3802701791602:ERROR:net/ocsp/nss_ocsp.cc(480)] No URLRequestContext for OCSP handler.
[27331:27411:3802701793380:ERROR:net/ocsp/nss_ocsp.cc(480)] No URLRequestContext for OCSP handler.
(pkix_CacheCertChain_Add: PKIX_PL_HashTable_Add for CertChain skipped: entry existed
[27331:27410:3802701794872:ERROR:net/ocsp/nss_ocsp.cc(480)] No URLRequestContext for OCSP handler.
(pkix_CacheCertChain_Add: PKIX_PL_HashTable_Add for CertChain skipped: entry existed
[japearson@agilepc04][~/Downloads] % google-chrome
(pkix_CacheCertChain_Add: PKIX_PL_HashTable_Add for CertChain skipped: entry existed
(pkix_CacheCertChain_Add: PKIX_PL_HashTable_Add for CertChain skipped: entry existed
Attempting to load libmoonloaderxpi 

It initially didn't work when the "No URLRequestContext for OCSP handler" errors were there.  I reopened google chrome and it worked, but logged those HashTable_Add messages.

What is strange is that [https://mail.google.com](https://mail.google.com) works fine but [https://chrome.google.com/](https://chrome.google.com/) doesn't

The only thing that is different between the 2 is the certificate issuer.  mail.google.com uses Thawte
and chrome.google.com uses: Google Internet Authority

So my suspicion is that the certificates issued by the Google Internet Authority are causing issues with Google Chrome with the underlying system libraries.  Since it seems that I ruled out a direct google chrome problem by installing the same version on an older machine.

Does anyone have the same problem?

I also posted this at: [http://www.google.com/support/forum/p/Chrome/thread?tid=460df49b523652fb&hl=en](http://www.google.com/support/forum/p/Chrome/thread?tid=460df49b523652fb&hl=en)

---

### Post by pearj on 2010-07-21
It seems I can partially get around this problem by adding the "Google Internet Authority" certificate to my nss database, but I still have problems with other sites, it's quite bizarre.

---

### Post by pearj on 2010-07-22
We recently changed Internet providers which seems to cause https issues for specific versions Chrome, I changed back to our old Internet provider and there are no problems.  Very weird.  I don't see why different ISP's could affect https. But something is causing google chrome grief.

---

