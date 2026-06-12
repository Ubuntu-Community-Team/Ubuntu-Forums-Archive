---
title: "Banshee crash in 11.04"
date: 2011-05-01
forum: General Help
---

### Post by baddnady23 on 2011-05-01
Anyone else been having an issue with banshee crashing when clicking the next track button?  When run from the terminal, this is the output that happens after I click next track...


```
[Warn  08:27:24.989] Caught an exception - Hyena.Data.Sqlite.SqliteException: Sqlite error 11: database disk image is malformed (SQL: DELETE FROM CoreSmartPlaylistEntries WHERE SmartPlaylistID = 6;
                  INSERT INTO CoreSmartPlaylistEntries
                    (EntryID, SmartPlaylistID, TrackID)
                    SELECT NULL, 6 as SmartPlaylistID, TrackId FROM CoreTracks,CoreArtists,CoreAlbums
                        WHERE CoreArtists.ArtistID = CoreTracks.ArtistID AND CoreAlbums.AlbumID = CoreTracks.AlbumID AND CoreTracks.PrimarySourceID = 1
                        AND (((CoreTracks.PlayCount = 0 AND CoreTracks.PlayCount IS NOT NULL) And (CoreTracks.SkipCount = 0 AND CoreTracks.SkipCount IS NOT NULL)))  ) (in `Hyena.Data.Sqlite')
  at Hyena.Data.Sqlite.Connection.CheckError (Int32 errorCode, System.String sql) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.Connection.Execute (System.String sql) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Hyena.Data.Sqlite.Connection connection) [0x00000] in <filename unknown>:0 

Unhandled Exception: Hyena.Data.Sqlite.SqliteException: Sqlite error 11: database disk image is malformed (SQL: DELETE FROM CoreSmartPlaylistEntries WHERE SmartPlaylistID = 6;
                  INSERT INTO CoreSmartPlaylistEntries
                    (EntryID, SmartPlaylistID, TrackID)
                    SELECT NULL, 6 as SmartPlaylistID, TrackId FROM CoreTracks,CoreArtists,CoreAlbums
                        WHERE CoreArtists.ArtistID = CoreTracks.ArtistID AND CoreAlbums.AlbumID = CoreTracks.AlbumID AND CoreTracks.PrimarySourceID = 1
                        AND (((CoreTracks.PlayCount = 0 AND CoreTracks.PlayCount IS NOT NULL) And (CoreTracks.SkipCount = 0 AND CoreTracks.SkipCount IS NOT NULL)))  )
  at Hyena.Data.Sqlite.Connection.CheckError (Int32 errorCode, System.String sql) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.Connection.Execute (System.String sql) [0x00000] in <filename unknown>:0 
  at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Hyena.Data.Sqlite.Connection connection) [0x00000] in <filename unknown>:0 

```

---

