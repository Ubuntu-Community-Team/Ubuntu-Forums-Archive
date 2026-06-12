---
title: "Rhythmbox crash with rhythmbox-ubuntuone-music-store plugin"
date: 2010-05-05
forum: General Help
---

### Post by Jonnhy on 2010-05-05
When a try rhythmbox in  the terminal I get thisn result

rhythmbox 
** (rhythmbox:2513): DEBUG: Loading the real store page

** (rhythmbox:2513): WARNING **: Syncdaemon already connected, not connecting again

liboauth: data to sign='GET&https%3A%2F%2Fone.ubuntu.com%2Fmusic%2Flogin&oauth_callback%3DNone%26oauth_consumer_key%3Dubuntuone%26oauth_nonce%3D6oEMZxRZWY3APZn5d9%26oauth_signature_method%3DHMAC-SHA1%26oauth_timestamp%3D1273113635%26oauth_token%3DLQCSwbBfwCd5FzQhFNvV%26oauth_verifier%3DNone%26oauth_version%3D1.0'


liboauth: key='hammertime&P8Pkbs2Tbrx9gQtpQ8BgdVv5FtxNsvWfVcb8HjZ91B5lv69zpTvT2NjKLvPpTV3G8NtPhNh1x7nktXC5'

** (rhythmbox:2513): DEBUG: navigation requested to [https://one.ubuntu.com/music/login?oauth_callback=None&oauth_consumer_key=ubuntuone&oauth_nonce=6oEMZxRZWY3APZn5d9&oauth_signature_method=HMAC-SHA1&oauth_timestamp=1273113635&oauth_token=LQCSwbBfwCd5FzQhFNvV&oauth_verifier=None&oauth_version=1.0&oauth_signature=n%2B3wb50qhTV8s55i5CF3wzsDTeg%3D](https://one.ubuntu.com/music/login?oauth_callback=None&oauth_consumer_key=ubuntuone&oauth_nonce=6oEMZxRZWY3APZn5d9&oauth_signature_method=HMAC-SHA1&oauth_timestamp=1273113635&oauth_token=LQCSwbBfwCd5FzQhFNvV&oauth_verifier=None&oauth_version=1.0&oauth_signature=n%2B3wb50qhTV8s55i5CF3wzsDTeg%3D)
Segmentation fault

if you uninstall the plugin rhythmbox-ubuntuone-music-store everything works fine.

Thanks for your help!

---

