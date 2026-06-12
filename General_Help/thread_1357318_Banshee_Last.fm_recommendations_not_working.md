---
title: "Banshee Last.fm recommendations not working"
date: 2009-12-17
forum: General Help
---

### Post by tylerannosaurus on 2009-12-17
So I've searched the web and can't seem to find anything about what the cause of this issue might be, but the recommendations that Banshee has in the player constantly says "loading" and nothing ever appears.

I ran debug with it in terminal and this is my output:

```
[Warn  01:43:10.867] Caught an exception - Address already in use (in `System')
  at System.Net.Sockets.Socket.Bind (System.Net.EndPoint local_end) [0x00000] 
  at Banshee.Web.BaseHttpServer.BindServerSocket () [0x00000] 
[Debug 01:43:10.869] DAAP Proxy listening for connections on port 46485
[Debug 01:43:23.395] Player state change: Idle -> Loading
[Debug 01:43:24.131] Player state change: Loading -> Loaded
[Warn  01:43:24.263] Caught an exception - Lastfm.Data.DataCore.CachePath and/or Lastfm.Data.DataCore.Useragent are null.  Applications must set this value. (in `Lastfm')
  at Lastfm.Data.DataCore.Initialize () [0x00000] 
  at Lastfm.Data.LastfmData`1[Lastfm.Data.SimilarArtist]..ctor (System.String dataUrlFragment, CacheDuration cacheDuration, System.String xpath) [0x00000] 
  at Lastfm.Data.LastfmData`1[Lastfm.Data.SimilarArtist]..ctor (System.String dataUrlFragment, System.String xpath) [0x00000] 
  at Lastfm.Data.LastfmArtistData.Get[SimilarArtist] (System.String fragment, System.String xpath) [0x00000] 
  at Lastfm.Data.LastfmArtistData.Get[SimilarArtist] (System.String fragment) [0x00000] 
  at Lastfm.Data.LastfmArtistData.get_SimilarArtists () [0x00000] 
  at Banshee.Lastfm.Recommendations.RecommendationPane.UpdateForArtist (System.String artist) [0x00000] 
[Info  01:43:24.265] Uncached artwork size 34 requested
[Debug 01:43:24.266] Player state change: Loaded -> Playing
[Debug 01:43:24.370] Creating Pango.Layout, configuring Cairo.Context
[Debug 01:43:24.372] Creating Pango.Layout, configuring Cairo.Context
[Debug 01:43:25.269] TrackInfoDisplay RenderAnimation: 25.00 FPS
[Debug 01:43:32.227] Audioscrobbler sign-on succeeded - Session ID received
[Debug 01:43:34.123] Submitted NowPlaying track to Audioscrobbler
```

Any thoughts?

Running Karmic with the kernel 2.6.31-17-generic, gnome 2.28.1

---

### Post by tylerannosaurus on 2009-12-17
I had tried uninstalling and purging before, but I tried again this time using the synaptic package manager. After re-installing, the recommendations work, so I'm not sure what the issue was, but it's working again.

---

