---
title: "How can I add a G723 codec to Linphone?"
date: 2011-06-25
forum: General Help
---

### Post by Sleepy-zz-John on 2011-06-25
I've installed the latest Linphone v3.4.3. on my Natty and successfully got one of my VOIP provider accounts (voipdiscount.com) working on it OK.

But now I'm having difficulty trying to add the UK based VOIP provider just-voip.net on my Linphone.  This account is working OK for me on their own app in Windows,  but not on my Natty Linphone.  just-voip.net have given me these details:

 ```

   1. Proxy server: 77.92.85.11:5060

   2. SIP Port:      5060

   3. Codec:         G729 or G723

   4. DTMF :         default

   5. Register:      Yes

   6. The User :    xxxxx

   7. Password:   yyyyyyyy
```

Having entered these details,  Linphone does give me a "Registration on SIP:77.92.85.11 successful" notification,  but when I try to dial the same number that works OK on my voipdiscount.com account, Linphone reports "User cannot be found at given address" 

Not sure but I suspect my problem may be lack of a G729 or G723 codec.   My Linphone settings Codecs tab only shows the following:

```

Name   Rate(Hz)  Status   Min bitrate (kb/s)  Parameters
speex  32000     Enabled  28.000000           vbr=on
speex  16000     Enabled  28.000000           vbr=on
speex   8000     Enabled   8.000000           vbr=on
GSM     8000     Enabled  13.500000
PCMU    8000     Enabled  64.000000
PCMA    8000     Enabled  64.000000 
```

I wonder if anyone can explain to me in fairly simple terms how I can add a G723 codec, please?     I've seen there are developers' references to both G729 and G723 in Linphone searches,  but no simple instructions or explanation that I can understand :confused:   It appears that G729 is subject to patent restrictions,  so that's why I thought I should choose G723 instead.

I'm also wondering if there really are major incompatibilities between speex and G723 that are causing my failure, or if I could be experiencing some entirely different problem,    so I'm open to any other suggestions.

---

