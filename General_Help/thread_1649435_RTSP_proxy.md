---
title: "RTSP proxy?"
date: 2010-12-20
forum: General Help
---

### Post by dbrb2 on 2010-12-20
I have two boxes on a single subnet

One is a webserver
The other is a video decoder that acts as an RTSP server

Currently, the webserver hosts a page that, amongst other things, includes a plugin to stream video from the codec to the page being viewed. 

However, I want to put the webserver onto a public IP address without needing to also give the decoder a public address. 

To do this I think I will need a setup whereby anyone attempting to initiate an rtsp stream to the webserver in fact initiiates a stream from the decoder - so the server is acting as a proxy

This dopesn't sound complicated, but neither can I work out how to cheive it. 

Any suggestions?

---

