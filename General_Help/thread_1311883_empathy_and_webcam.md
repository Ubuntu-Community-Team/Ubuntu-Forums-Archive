---
title: "empathy and webcam"
date: 2009-11-02
forum: General Help
---

### Post by alanrr_sr on 2009-11-02
Hi,

I am able to use my webcam with cheese and with skype using preloading, but I am not able to use it in empathy, calling another empathy client (same ubuntu version). The webcam button is disabled and the only thing that I see is a black image. Any hints?

Webcam: 
Bus 005 Device 003: ID 05a9:a511 OmniVision Technologies, Inc. OV511+ Webcam



```

(empathy:6422): tp-fs-DEBUG: calling MediaSessionHandler::Ready
(empathy:6422): tp-fs-DEBUG: New stream, stream_id=1, media_type=0, direction=3
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) get_all_properties_cb: Adding STUN server 64.233.169.126:19302
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) get_all_properties_cb: Adding relay (udp) 74.125.65.126:19295 smTzlskqY6QvUMP8:1eTqLCU6vMhSJ95h 1
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) get_all_properties_cb: Adding relay (tcp) 74.125.65.126:19294 smTzlskqY6QvUMP8:1eTqLCU6vMhSJ95h 1
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) get_all_properties_cb: Adding relay (tls) 74.125.65.126:443 smTzlskqY6QvUMP8:1eTqLCU6vMhSJ95h 1
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) get_all_properties_cb: Adding relay (udp) 209.85.163.126:19295 mJ43UG0m4XepyTKd:xQyWf3eBc3DUgRCr 2
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) get_all_properties_cb: Adding relay (tcp) 209.85.163.126:19294 mJ43UG0m4XepyTKd:xQyWf3eBc3DUgRCr 2
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) get_all_properties_cb: Adding relay (tls) 209.85.163.126:443 mJ43UG0m4XepyTKd:xQyWf3eBc3DUgRCr 2
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) _tf_stream_try_sending_codecs: called (send_local:1 send_supported:0)
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) _tf_stream_try_sending_codecs: 102: audio SPEEX clock:8000 channels:1
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) _tf_stream_try_sending_codecs: 103: audio SPEEX clock:16000 channels:1
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) _tf_stream_try_sending_codecs: 96: audio SIREN clock:16000 channels:0 bitrate=16000
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) _tf_stream_try_sending_codecs: 0: audio PCMU clock:8000 channels:0
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) _tf_stream_try_sending_codecs: 8: audio PCMA clock:8000 channels:0
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) _tf_stream_try_sending_codecs: 3: audio GSM clock:8000 channels:0
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) _tf_stream_try_sending_codecs: 99: audio telephone-event clock:16000 channels:0 events=0-15
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) _tf_stream_try_sending_codecs: 100: audio telephone-event clock:8000 channels:0 events=0-15
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) fs_codecs_to_tp: adding codec SPEEX [102]
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) fs_codecs_to_tp: adding codec SPEEX [103]
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) fs_codecs_to_tp: adding codec SIREN [96]
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) fs_codecs_to_tp: adding codec PCMU [0]
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) fs_codecs_to_tp: adding codec PCMA [8]
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) fs_codecs_to_tp: adding codec GSM [3]
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) fs_codecs_to_tp: adding codec telephone-event [99]
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) fs_codecs_to_tp: adding codec telephone-event [100]
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) _tf_stream_try_sending_codecs: calling MediaStreamHandler::Ready
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) cb_fs_new_local_candidate: called
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) cb_fs_new_local_candidate: called
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) _tf_stream_bus_message: Codecs changed
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) _tf_stream_try_sending_codecs: called (send_local:0 send_supported:0)
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) _tf_stream_try_sending_codecs: 102: audio SPEEX clock:8000 channels:1
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) _tf_stream_try_sending_codecs: 103: audio SPEEX clock:16000 channels:1
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) _tf_stream_try_sending_codecs: 96: audio SIREN clock:16000 channels:0 bitrate=16000
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) _tf_stream_try_sending_codecs: 0: audio PCMU clock:8000 channels:0
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) _tf_stream_try_sending_codecs: 8: audio PCMA clock:8000 channels:0
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) _tf_stream_try_sending_codecs: 3: audio GSM clock:8000 channels:0
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) _tf_stream_try_sending_codecs: 99: audio telephone-event clock:16000 channels:0 events=0-15
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) _tf_stream_try_sending_codecs: 100: audio telephone-event clock:8000 channels:0 events=0-15
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) set_stream_playing: 0
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) set_stream_sending: 0
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) cb_fs_new_local_candidate: called
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) cb_fs_new_local_candidate: called
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) cb_fs_new_local_candidate: called
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) cb_fs_new_local_candidate: called
(empathy:6422): tp-fs-DEBUG: New stream, stream_id=2, media_type=1, direction=3
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) get_all_properties_cb: Adding STUN server 64.233.169.126:19302
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) get_all_properties_cb: Adding relay (udp) 209.85.163.126:19295 fmiTSX2qLgmI1MHh:emASeoS1qeFJgPUW 1
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) get_all_properties_cb: Adding relay (tcp) 209.85.163.126:19294 fmiTSX2qLgmI1MHh:emASeoS1qeFJgPUW 1
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) get_all_properties_cb: Adding relay (tls) 209.85.163.126:443 fmiTSX2qLgmI1MHh:emASeoS1qeFJgPUW 1
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) get_all_properties_cb: Adding relay (udp) 74.125.47.126:19295 TakDULRN2HZMurwu:319iqGTCRxUPzqm4 2
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) get_all_properties_cb: Adding relay (tcp) 74.125.47.126:19294 TakDULRN2HZMurwu:319iqGTCRxUPzqm4 2
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) get_all_properties_cb: Adding relay (tls) 74.125.47.126:443 TakDULRN2HZMurwu:319iqGTCRxUPzqm4 2
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) _tf_stream_try_sending_codecs: called (send_local:1 send_supported:0)
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) _tf_stream_try_sending_codecs: 97: video H264 clock:90000 channels:0
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) _tf_stream_try_sending_codecs: 34: video H263 clock:90000 channels:0
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) _tf_stream_try_sending_codecs: 96: video THEORA clock:90000 channels:0 delivery-method=inline
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) _tf_stream_try_sending_codecs: 32: video MPV clock:90000 channels:0
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) _tf_stream_try_sending_codecs: 26: video JPEG clock:90000 channels:0
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) _tf_stream_try_sending_codecs: 98: video H263-1998 clock:90000 channels:0
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) _tf_stream_try_sending_codecs: 99: video DV clock:90000 channels:0
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) fs_codecs_to_tp: adding codec H264 [97]
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) fs_codecs_to_tp: adding codec H263 [34]
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) fs_codecs_to_tp: adding codec THEORA [96]
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) fs_codecs_to_tp: adding codec MPV [32]
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) fs_codecs_to_tp: adding codec JPEG [26]
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) fs_codecs_to_tp: adding codec H263-1998 [98]
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) fs_codecs_to_tp: adding codec DV [99]
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) _tf_stream_try_sending_codecs: calling MediaStreamHandler::Ready
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) set_stream_playing: 0
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) set_stream_sending: 0
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) _tf_stream_bus_message: Codecs changed
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) _tf_stream_try_sending_codecs: called (send_local:0 send_supported:0)
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) _tf_stream_try_sending_codecs: 97: video H264 clock:90000 channels:0
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) _tf_stream_try_sending_codecs: 34: video H263 clock:90000 channels:0
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) _tf_stream_try_sending_codecs: 96: video THEORA clock:90000 channels:0 delivery-method=inline
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) _tf_stream_try_sending_codecs: 32: video MPV clock:90000 channels:0
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) _tf_stream_try_sending_codecs: 26: video JPEG clock:90000 channels:0
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) _tf_stream_try_sending_codecs: 98: video H263-1998 clock:90000 channels:0
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) _tf_stream_try_sending_codecs: 99: video DV clock:90000 channels:0
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) cb_fs_new_local_candidate: called
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) cb_fs_new_local_candidate: called
empathy-Message: Element error: Não foi possível obter/atribuir configurações do/ao recurso. -- v4l_calls.c(424): gst_v4l_set_chan_norm (): /GstPipeline:pipeline0/EmpathyGstVideoSrc:empathygstvideosrc0/GstGConfVideoSrc:gconfvideosrc0/GstBin:bin8/GstV4lSrc:v4lsrc0:
Error getting the channel/norm settings: Argumento inválido

(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) cb_fs_new_local_candidate: called
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) cb_fs_new_local_candidate: called
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) cb_fs_new_local_candidate: called
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) cb_fs_new_local_candidate: called
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) cb_fs_new_local_candidate: called
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) cb_fs_new_local_candidate: called
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) cb_fs_new_local_candidate: called
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) cb_fs_new_local_candidate: called
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) cb_fs_new_local_candidate: called
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) cb_fs_new_local_candidate: called
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) cb_fs_new_local_candidate: called
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) cb_fs_new_local_candidate: called
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) cb_fs_local_candidates_prepared: called
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) cb_fs_local_candidates_prepared: candidate->ip = '192.168.1.100'
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) cb_fs_local_candidates_prepared: candidate->ip = '192.168.1.100'
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) cb_fs_local_candidates_prepared: candidate->ip = '201.53.192.19'
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) cb_fs_local_candidates_prepared: candidate->ip = '201.53.192.19'
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) cb_fs_local_candidates_prepared: candidate->ip = '74.125.65.126'
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) cb_fs_local_candidates_prepared: candidate->ip = '209.85.163.126'
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) cb_fs_local_candidates_prepared: candidate->ip = '209.85.163.126'
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) cb_fs_local_candidates_prepared: candidate->ip = '74.125.65.126'
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) cb_fs_local_candidates_prepared: candidate->ip = '74.125.65.126'
(empathy:6422): tp-fs-DEBUG: stream 1 0x23d5a70 (audio) cb_fs_local_candidates_prepared: candidate->ip = '209.85.163.126'
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) cb_fs_local_candidates_prepared: called
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) cb_fs_local_candidates_prepared: candidate->ip = '192.168.1.100'
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) cb_fs_local_candidates_prepared: candidate->ip = '192.168.1.100'
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) cb_fs_local_candidates_prepared: candidate->ip = '201.53.192.19'
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) cb_fs_local_candidates_prepared: candidate->ip = '201.53.192.19'
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) cb_fs_local_candidates_prepared: candidate->ip = '74.125.47.126'
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) cb_fs_local_candidates_prepared: candidate->ip = '209.85.163.126'
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) cb_fs_local_candidates_prepared: candidate->ip = '74.125.47.126'
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) cb_fs_local_candidates_prepared: candidate->ip = '209.85.163.126'
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) cb_fs_local_candidates_prepared: candidate->ip = '74.125.47.126'
(empathy:6422): tp-fs-DEBUG: stream 2 0x23d5e30 (video) cb_fs_local_candidates_prepared: candidate->ip = '209.85.163.126'
empathy-Message: Element error: Não foi possível sincronizar no recurso. -- v4lsrc_calls.c(124): gst_v4lsrc_sync_frame (): /GstPipeline:pipeline0/EmpathyGstVideoSrc:empathygstvideosrc0/GstGConfVideoSrc:gconfvideosrc0/GstBin:bin8/GstV4lSrc:v4lsrc0:
system error: Argumento inválido

empathy-Message: Element error: Não foi possível sincronizar no recurso. -- v4lsrc_calls.c(124): gst_v4lsrc_sync_frame (): /GstPipeline:pipeline0/EmpathyGstVideoSrc:empathygstvideosrc0/GstGConfVideoSrc:gconfvideosrc0/GstBin:bin8/GstV4lSrc:v4lsrc0:
system error: Argumento inválido

empathy-Message: Element error: Não foi possível sincronizar no recurso. -- v4lsrc_calls.c(124): gst_v4lsrc_sync_frame (): /GstPipeline:pipeline0/EmpathyGstVideoSrc:empathygstvideosrc0/GstGConfVideoSrc:gconfvideosrc0/GstBin:bin8/GstV4lSrc:v4lsrc0:
system error: Argumento inválido

(empathy:6422): tp-fs-DEBUG: tf_channel_dispose
tp-fs-Message: tf_stream_error: stream error errorno=0 error=UI stopped channel
tp-fs-Message: tf_stream_error: stream error errorno=0 error=UI stopped channel
(empathy:6422): tp-fs-DEBUG: _tf_session_dispose

(empathy:6422): GLib-GObject-WARNING **: invalid cast from `PangoLayout' to `GtkImage'

(empathy:6422): Gtk-CRITICAL **: gtk_image_set_from_pixbuf: assertion `GTK_IS_IMAGE (image)' failed

(empathy:6422): GLib-GObject-WARNING **: invalid cast from `PangoLayout' to `GtkImage'

(empathy:6422): Gtk-CRITICAL **: gtk_image_set_from_pixbuf: assertion `GTK_IS_IMAGE (image)' failed


```

---

