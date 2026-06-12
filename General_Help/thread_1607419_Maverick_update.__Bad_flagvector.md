---
title: "Maverick update.  Bad flagvector"
date: 2010-10-27
forum: General Help
---

### Post by amalgamas on 2010-10-27
After my update from 10.04 to 10.10 I seem to get errors when I save files in the terminal using gedit or when opening and closing Rhythmbox.  I probably get the errors in other situations as well, I haven't done thorough checking.

Opening Rhythmbox from the terminal produces the following message:
```

bf@bf-laptop:~$ rhythmbox 2>xxx
** (rhythmbox:3235): DEBUG: Syncdaemon not running, waiting for it to start in NameOwnerChanged
** (rhythmbox:3235): DEBUG: Loading the real store page
** (rhythmbox:3235): DEBUG: navigation requested to https://one.ubuntu.com/music/login?oauth_callback=None&oauth_consumer_key=ubuntuone&oauth_nonce=jw5697zOP0R8x0bN0gGDqhT&oauth_signature_method=HMAC-SHA1&oauth_timestamp=1288214591&oauth_token=pQtNhQ3PnRNrXd7NV641&oauth_verifier=None&oauth_version=1.0&oauth_signature=irNH%2BgNu9uppYR7wOBdniyKiQf8%3D
** (rhythmbox:3235): DEBUG: navigation requested to http://stores.7digital.com/user/partnerLogin.aspx?shop=436&returnUrl=http%3A%2F%2Fstores.7digital.com%2Fdefault.aspx%3Fshop%3D436%26partner%3D983&oauth_nonce=98179146&oauth_timestamp=1288214594&oauth_signature_method=HMAC-SHA1&oauth_consumer_key=canonical&userid=196607&oauth_version=1.0&oauth_signature=NwQdLmm6B4MKAI6L8NuZ8JTBtqw%3D&partner=983
** (rhythmbox:3235): DEBUG: navigation requested to http://stores.7digital.com/default.aspx?shop=436&partner=983

```And then 80825 lines of screen output looking like these:
```

** Message: pygobject_register_sinkfunc is deprecated (GstObject)
error: line 4: bad flagvector
error: line 5: bad flagvector
error: line 7: bad flagvector
error: line 8: bad flagvector
error: line 9: bad flagvector
error: line 10: bad flagvector
error: line 11: bad flagvector
error: line 12: bad flagvector
...
...
...
error: line 322036: bad flagvector
error: line 322037: bad flagvector
error: line 322039: bad flagvector
error: line 322040: bad flagvector
error: line 322044: bad flagvector

liboauth: data to sign='GET&https%3A%2F%2Fone.ubuntu.com%2Fmusic%2Flogin&oauth_callback%3DNone%26oauth_consumer_key%3Dubuntuone%26oauth_nonce%3Djw5697zOP0R8x0bN0gGDqhT%26oauth_signature_method%3DHMAC-SHA1%26oauth_timestamp%3D1288214591%26oauth_token%3DpQtNhQ3PnRNrXd7NV641%26oauth_verifier%3DNone%26oauth_version%3D1.0'


liboauth: key='hammertime&hDzw5z0w02k1ZNWn7q1WRmRxKVGtCldJ2Wn0hGrn1C2pn9xKvd5fRTN1x51TP99hZKpD12lJkdmSk7D1'

```
I hope somebody can help me figure out what is wrong and what to do.

---

