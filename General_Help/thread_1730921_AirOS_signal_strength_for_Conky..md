---
title: "AirOS signal strength for Conky."
date: 2011-04-16
forum: General Help
---

### Post by jpmeijers on 2011-04-16
If you own an Ubiquity NanoStation or any other router running AirOS, you might find this line handy. It displays your wifi signal strength and noise floor inside conky. Just add it to your .conkyrc file.

```
WiFi: $alignr${execi 1 wget --user=<username> --password=<password> -O – [http://192.168.1.20/signal.cgi](http://192.168.1.20/signal.cgi) -q -O - | sed -e 's/signal=/Signal: /' -e 's/ noisef=/ Noise: /' -e 's/;/dBm,/' -e 's/;/dBm/'
}${alignr}
```

Where username and password are the login details to access your router's web configuration and 192.168.1.20 is the router's IP address.

---

