---
title: "Digital camera and Rhythmbox conflicts."
date: 2010-06-02
forum: General Help
---

### Post by stevedes on 2010-06-02
Ok I use Ubuntu 10.04 on Wubi.
Just today, i connected and switched on my digital camera while playing music on rhythmbox. The camera didn't mount and the rhythmbox window stopped responding but it starts responding the moment i switch off the camera.(a note: the music does not stop playing)

If I first turn on the camera and then start rhythmbox, it just doesn't start.

Terminal output for rhythmbox when switching on camera while rhythmbox is running:
```
** (rhythmbox:3622): DEBUG: Loading the real store page

** (rhythmbox:3622): WARNING **: Syncdaemon already connected, not connecting again

liboauth: data to sign='GET&https%3A%2F%2Fone.ubuntu.com%2Fmusic%2Flogin&oauth_callback%3DNone%26oauth_consumer_key%3Dubuntuone%26oauth_nonce%3DmT5s6GWqVu_tfm1szuMCy%26oauth_signature_method%3DHMAC-SHA1%26oauth_timestamp%3D1275492419%26oauth_token%3DGwwxHclq7RSxkm60QXLf%26oauth_verifier%3DNone%26oauth_version%3D1.0'


liboauth: key='hammertime&3rh3gpSfvQHhPJCnSBsQ21j25fG89mP8vzCh28m8p1dH2VvCC8vPgfLzSRpT1XPZCB8RN1BX9qNlv6wb'

** (rhythmbox:3622): DEBUG: navigation requested to https://one.ubuntu.com/music/login?oauth_callback=None&oauth_consumer_key=ubuntuone&oauth_nonce=mT5s6GWqVu_tfm1szuMCy&oauth_signature_method=HMAC-SHA1&oauth_timestamp=1275492419&oauth_token=GwwxHclq7RSxkm60QXLf&oauth_verifier=None&oauth_version=1.0&oauth_signature=kR%2Fljr4AOSGwfYGMpHryeSA6LGQ%3D
** (rhythmbox:3622): DEBUG: navigation requested to http://stores.7digital.com/user/partnerLogin.aspx?shop=496&returnUrl=http%3A%2F%2Fstores.7digital.com%2Fdefault.aspx%3Fshop%3D496%26partner%3D983&oauth_nonce=43875246&oauth_timestamp=1275492422&oauth_signature_method=HMAC-SHA1&oauth_consumer_key=canonical&userid=359691&oauth_version=1.0&oauth_signature=w92nn5XbDRHPZ9eqVeyoL5KebZw%3D&partner=983
** (rhythmbox:3622): DEBUG: navigation requested to http://stores.7digital.com/default.aspx?shop=496&partner=983
Device 0 (VID=040a and PID=05ce) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team
LIBMTP PANIC: could not inspect object property descriptions!
```Terminal output of rhythmbox if launched while the camera is switched on.
```
** (rhythmbox:3686): DEBUG: Loading the real store page

** (rhythmbox:3686): WARNING **: Syncdaemon already connected, not connecting again

liboauth: data to sign='GET&https%3A%2F%2Fone.ubuntu.com%2Fmusic%2Flogin&oauth_callback%3DNone%26oauth_consumer_key%3Dubuntuone%26oauth_nonce%3DVrMwkY6oOdKwe9zt2WACshm4pqCZQ%26oauth_signature_method%3DHMAC-SHA1%26oauth_timestamp%3D1275492634%26oauth_token%3DGwwxHclq7RSxkm60QXLf%26oauth_verifier%3DNone%26oauth_version%3D1.0'


liboauth: key='hammertime&3rh3gpSfvQHhPJCnSBsQ21j25fG89mP8vzCh28m8p1dH2VvCC8vPgfLzSRpT1XPZCB8RN1BX9qNlv6wb'

** (rhythmbox:3686): DEBUG: navigation requested to https://one.ubuntu.com/music/login?oauth_callback=None&oauth_consumer_key=ubuntuone&oauth_nonce=VrMwkY6oOdKwe9zt2WACshm4pqCZQ&oauth_signature_method=HMAC-SHA1&oauth_timestamp=1275492634&oauth_token=GwwxHclq7RSxkm60QXLf&oauth_verifier=None&oauth_version=1.0&oauth_signature=GaB2hXCmgwh4pvJ1kImhZMSxxo4%3D
Device 0 (VID=040a and PID=05ce) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team
Device 0 (VID=040a and PID=05ce) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team
Device 0 (VID=040a and PID=05ce) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team
Device 0 (VID=040a and PID=05ce) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team
Device 0 (VID=040a and PID=05ce) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team
Device 0 (VID=040a and PID=05ce) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team
ignoring usb_claim_interface = -16ignoring usb_claim_interface = -22PTP_ERROR_IO: Trying again after re-initializing USB interface
inep: usb_get_endpoint_status(): Device or resource busy
outep: usb_get_endpoint_status(): Device or resource busy
usb_clear_halt() on IN endpoint: Device or resource busy
usb_clear_halt() on OUT endpoint: Device or resource busy
usb_clear_halt() on INTERRUPT endpoint: Device or resource busy
LIBMTP PANIC: could not inspect object property descriptions!
```Any help?

---

### Post by stevedes on 2010-06-05
Nobody???

---

### Post by ElSlunko on 2010-06-16
I have the same issue.

---

