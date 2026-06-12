---
title: "Bad flagvector"
date: 2010-10-26
forum: General Help
---

### Post by amalgamas on 2010-10-26
After my ubuntu 10.04 to 10.10 upgrade I have noticed some strange error messages: when I save files from gedit (opened from the terminal) I get a string of error message lines running over the terminal window before the file is saved, seemingly without any error (and lucky so, the file was fstab!).

I checked around a little bit and when I open Rhythmbox from the terminal I get the same string of error lines before Rhythmbox opens without further problems.

I suppose I'll get the same error messages with other programs also.

I supply some ef the output from the terminal

I need help, any suggestions?

> 
...
error: line 321988: bad flagvector
error: line 321989: bad flagvector
error: line 321990: bad flagvector
error: line 321993: bad flagvector
error: line 321997: bad flagvector
error: line 321999: bad flagvector
error: line 322000: bad flagvector
error: line 322001: bad flagvector
error: line 322003: bad flagvector
error: line 322004: bad flagvector
error: line 322005: bad flagvector
error: line 322011: bad flagvector
error: line 322018: bad flagvector
error: line 322024: bad flagvector
error: line 322029: bad flagvector
error: line 322033: bad flagvector
error: line 322034: bad flagvector
error: line 322035: bad flagvector
error: line 322036: bad flagvector
error: line 322037: bad flagvector
error: line 322039: bad flagvector
error: line 322040: bad flagvector
error: line 322044: bad flagvector
** (rhythmbox:3550): DEBUG: Loading the real store page

liboauth: data to sign='GET&https%3A%2F%2Fone.ubuntu.com%2Fmusic%2Flogin&oauth_callback%3DNone%26oauth_consumer_key%3Dubuntuone%26oauth_nonce%3Dbdq3SU66d_YlDUJYcQ8ReFX%26oauth_signature_method%3DHMAC-SHA1%26oauth_timestamp%3D1288122660%26oauth_token%3DpQtNhQ3PnRNrXd7NV641%26oauth_verifier%3DNone%26oauth_version%3D1.0'


liboauth: key='hammertime&hDzw5z0w02k1ZNWn7q1WRmRxKVGtCldJ2Wn0hGrn1C2pn9xKvd5fRTN1x51TP99hZKpD12lJkdmSk7D1'

** (rhythmbox:3550): DEBUG: navigation requested to [https://one.ubuntu.com/music/login?oauth_callback=None&oauth_consumer_key=ubuntuone&oauth_nonce=bdq3SU66d_YlDUJYcQ8ReFX&oauth_signature_method=HMAC-SHA1&oauth_timestamp=1288122660&oauth_token=pQtNhQ3PnRNrXd7NV641&oauth_verifier=None&oauth_version=1.0&oauth_signature=pe5wVU2VxjMwvbewOAMHPcH5nxk%3D](https://one.ubuntu.com/music/login?oauth_callback=None&oauth_consumer_key=ubuntuone&oauth_nonce=bdq3SU66d_YlDUJYcQ8ReFX&oauth_signature_method=HMAC-SHA1&oauth_timestamp=1288122660&oauth_token=pQtNhQ3PnRNrXd7NV641&oauth_verifier=None&oauth_version=1.0&oauth_signature=pe5wVU2VxjMwvbewOAMHPcH5nxk%3D)
** (rhythmbox:3550): DEBUG: navigation requested to [http://stores.7digital.com/user/partnerLogin.aspx?shop=436&returnUrl=http%3A%2F%2Fstores.7digital.com%2Fdefault.aspx%3Fshop%3D436%26partner%3D983&oauth_nonce=53299650&oauth_timestamp=1288122663&oauth_signature_method=HMAC-SHA1&oauth_consumer_key=canonical&userid=196607&oauth_version=1.0&oauth_signature=1US7ywDU%2F8Ce9vzkSs%2B1QxsWuRY%3D&partner=983](http://stores.7digital.com/user/partnerLogin.aspx?shop=436&returnUrl=http%3A%2F%2Fstores.7digital.com%2Fdefault.aspx%3Fshop%3D436%26partner%3D983&oauth_nonce=53299650&oauth_timestamp=1288122663&oauth_signature_method=HMAC-SHA1&oauth_consumer_key=canonical&userid=196607&oauth_version=1.0&oauth_signature=1US7ywDU%2F8Ce9vzkSs%2B1QxsWuRY%3D&partner=983)
** (rhythmbox:3550): DEBUG: navigation requested to [http://stores.7digital.com/default.aspx?shop=436&partner=983](http://stores.7digital.com/default.aspx?shop=436&partner=983)


---

