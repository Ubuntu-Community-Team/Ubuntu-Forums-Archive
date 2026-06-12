---
title: "Installing VLC 1.1.11 || Lucid 64"
date: 2011-07-26
forum: General Help
---

### Post by linuxyogi on 2011-07-26
Hi, 

I am trying to compile & install vlc 1.1.11 under Lucid.

./configure completes without any errors but make prints
```

   CC     libvlccore_la-revision.lo
  CCLD   libvlccore.la
  CC     control/libvlc_la-core.lo
  CC     control/libvlc_la-error.lo
  CC     control/libvlc_la-log.lo
  CC     control/libvlc_la-playlist.lo
  CC     control/libvlc_la-vlm.lo
  CC     control/libvlc_la-video.lo
control/video.c:169:2: warning: #warning Not thread-safe!
control/video.c: In function 'get_object':
control/video.c:609: warning: 'vlc_object_find_name' is deprecated (declared at ../include/vlc_objects.h:78)
  CC     control/libvlc_la-audio.lo
  CC     control/libvlc_la-event.lo
  CC     control/libvlc_la-event_async.lo
  CC     control/libvlc_la-media.lo
  CC     control/libvlc_la-media_player.lo
control/media_player.c: In function 'input_event_changed':
control/media_player.c:225: warning: unused parameter 'psz_cmd'
control/media_player.c: In function 'libvlc_media_player_get_nsobject':
control/media_player.c:820: warning: unused parameter 'p_mi'
control/media_player.c: In function 'libvlc_media_player_get_agl':
control/media_player.c:846: warning: unused parameter 'p_mi'
control/media_player.c: In function 'libvlc_media_player_get_hwnd':
control/media_player.c:891: warning: unused parameter 'p_mi'
  CC     control/libvlc_la-media_list.lo
control/media_list.c:272:2: warning: #warning Missing error handling!
  CC     control/libvlc_la-media_list_player.lo
  CC     control/libvlc_la-media_library.lo
control/media_library.c: In function 'libvlc_media_library_load':
control/media_library.c:132: warning: 'libvlc_media_list_add_file_content' is deprecated (declared at ../include/vlc/libvlc_media_list.h:70)
  CC     control/libvlc_la-media_discoverer.lo
  CC     libvlc_la-revision.lo
  CCLD   libvlc.la
  GEN    libvlc.pc
config.status: creating src/libvlc.pc
  GEN    vlc-plugin.pc
config.status: creating src/vlc-plugin.pc
make[4]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/src'
Making all in test
make[4]: Entering directory `/home/tux/Downloads/vlc-1.1.11/src/test'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/src/test'
make[3]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/src'
make[2]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/src'
Making all in libs/srtp
make[2]: Entering directory `/home/tux/Downloads/vlc-1.1.11/libs/srtp'
  CC     srtp.lo
  CCLD   libvlc_srtp.la
make[2]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/libs/srtp'
Making all in libs/unzip
make[2]: Entering directory `/home/tux/Downloads/vlc-1.1.11/libs/unzip'
  CC     unzip.lo
  CC     ioapi.lo
  CCLD   libunzip.la
make[2]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/libs/unzip'
Making all in bin
make[2]: Entering directory `/home/tux/Downloads/vlc-1.1.11/bin'
  CC     vlc.o
vlc.c: In function &#8216;main&#8217;:
vlc.c:194: warning: &#8216;libvlc_playlist_play&#8217; is deprecated (declared at ../include/vlc/deprecated.h:59)
  CC     override.o
  CCLD   vlc
  CC     rootwrap.o
  CCLD   vlc-wrapper
  CC     vlc_static-vlc.o
vlc.c: In function &#8216;main&#8217;:
vlc.c:194: warning: &#8216;libvlc_playlist_play&#8217; is deprecated (declared at ../include/vlc/deprecated.h:59)
  CC     vlc_static-override.o
  CCLD   vlc-static
  CC     cachegen.o
  CCLD   vlc-cache-gen
make[2]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/bin'
Making all in modules
make[2]: Entering directory `/home/tux/Downloads/vlc-1.1.11/modules'
Making all in access
make[3]: Entering directory `/home/tux/Downloads/vlc-1.1.11/modules/access'
make  all-recursive
make[4]: Entering directory `/home/tux/Downloads/vlc-1.1.11/modules/access'
Making all in dvb
make[5]: Entering directory `/home/tux/Downloads/vlc-1.1.11/modules/access/dvb'
make  all-am
make[6]: Entering directory `/home/tux/Downloads/vlc-1.1.11/modules/access/dvb'
  CC     libdvb_plugin_la-access.lo
In file included from dvb.h:27,
                 from access.c:75:
scan.h:36:5: warning: #warning NIT is not supported by your libdvbpsi version
access.c: In function 'ParseMRL':
access.c:938: warning: ignoring return value of 'strtol', declared with attribute warn_unused_result
  CC     libdvb_plugin_la-scan.lo
In file included from dvb.h:27,
                 from scan.c:67:
scan.h:36:5: warning: #warning NIT is not supported by your libdvbpsi version
scan.c: In function 'scan_session_Clean':
scan.c:630: warning: pointer targets in passing argument 1 of 'dvbsi_to_utf8' differ in signedness
dvb.h:243: note: expected 'const char *' but argument is of type 'uint8_t *'
  CC     libdvb_plugin_la-linux_dvb.lo
In file included from dvb.h:27,
                 from linux_dvb.c:74:
scan.h:36:5: warning: #warning NIT is not supported by your libdvbpsi version
linux_dvb.c: In function 'FrontendSetQAM':
linux_dvb.c:1116: warning: comparison between signed and unsigned integer expressions
linux_dvb.c:1117: warning: comparison between signed and unsigned integer expressions
linux_dvb.c: In function 'FrontendSet':
linux_dvb.c:937: warning: call to 'harmful_delay' declared with attribute warning: use proper event handling instead of short delay
linux_dvb.c:986: warning: call to 'harmful_delay' declared with attribute warning: use proper event handling instead of short delay
  CC     libdvb_plugin_la-en50221.lo
In file included from dvb.h:27,
                 from en50221.c:72:
scan.h:36:5: warning: #warning NIT is not supported by your libdvbpsi version
en50221.c: In function 'dvbsi_to_utf8':
en50221.c:2448: warning: ignoring return value of 'vlc_iconv', declared with attribute warn_unused_result
en50221.c: In function 'en50221_Init':
en50221.c:1900: warning: call to 'harmful_delay' declared with attribute warning: use proper event handling instead of short delay
  CC     libdvb_plugin_la-http.lo
In file included from dvb.h:27,
                 from http.c:66:
scan.h:36:5: warning: #warning NIT is not supported by your libdvbpsi version
  CCLD   libdvb_plugin.la
make[6]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/modules/access/dvb'
make[5]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/modules/access/dvb'
Making all in mms
make[5]: Entering directory `/home/tux/Downloads/vlc-1.1.11/modules/access/mms'
make  all-am
make[6]: Entering directory `/home/tux/Downloads/vlc-1.1.11/modules/access/mms'
  CC     libaccess_mms_plugin_la-mms.lo
  CC     libaccess_mms_plugin_la-mmsh.lo
  CC     libaccess_mms_plugin_la-mmstu.lo
mmstu.c: In function 'KeepAliveThread':
mmstu.c:1573: warning: no return statement in function returning non-void
mmstu.c: In function 'mms_CommandRead':
mmstu.c:1466: warning: call to 'harmful_delay' declared with attribute warning: use proper event handling instead of short delay
mmstu.c: In function 'mms_HeaderMediaRead':
mmstu.c:1519: warning: call to 'harmful_delay' declared with attribute warning: use proper event handling instead of short delay
  CC     libaccess_mms_plugin_la-buffer.lo
buffer.c: In function 'var_buffer_addUTF16':
buffer.c:124: warning: ignoring return value of 'vlc_iconv', declared with attribute warn_unused_result
  CC     libaccess_mms_plugin_la-asf.lo
  CCLD   libaccess_mms_plugin.la
make[6]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/modules/access/mms'
make[5]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/modules/access/mms'
Making all in rtp
make[5]: Entering directory `/home/tux/Downloads/vlc-1.1.11/modules/access/rtp'
make  all-am
make[6]: Entering directory `/home/tux/Downloads/vlc-1.1.11/modules/access/rtp'
  CC     librtp_plugin_la-rtp.lo
  CC     librtp_plugin_la-input.lo
input.c: In function 'rtp_stream_recv':
input.c:85: warning: variable 'len' might be clobbered by 'longjmp' or 'vfork'
input.c:98: warning: variable 'block' might be clobbered by 'longjmp' or 'vfork'
input.c:101: warning: variable 'i' might be clobbered by 'longjmp' or 'vfork'
  CC     librtp_plugin_la-session.lo
  CCLD   librtp_plugin.la
make[6]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/modules/access/rtp'
make[5]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/modules/access/rtp'
Making all in rtsp
make[5]: Entering directory `/home/tux/Downloads/vlc-1.1.11/modules/access/rtsp'
make  all-am
make[6]: Entering directory `/home/tux/Downloads/vlc-1.1.11/modules/access/rtsp'
make[6]: Nothing to be done for `all-am'.
make[6]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/modules/access/rtsp'
make[5]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/modules/access/rtsp'
Making all in vcd
make[5]: Entering directory `/home/tux/Downloads/vlc-1.1.11/modules/access/vcd'
make  all-am
make[6]: Entering directory `/home/tux/Downloads/vlc-1.1.11/modules/access/vcd'
  CC     libvcd_plugin_la-vcd.lo
vcd.c: In function 'Block':
vcd.c:390: warning: comparison between signed and unsigned integer expressions
vcd.c: In function 'Seek':
vcd.c:424: warning: comparison between signed and unsigned integer expressions
  CC     libvcd_plugin_la-cdrom.lo
  CCLD   libvcd_plugin.la
make[6]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/modules/access/vcd'
make[5]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/modules/access/vcd'
Making all in vcdx
make[5]: Entering directory `/home/tux/Downloads/vlc-1.1.11/modules/access/vcdx'
make  all-am
make[6]: Entering directory `/home/tux/Downloads/vlc-1.1.11/modules/access/vcdx'
make[6]: Nothing to be done for `all-am'.
make[6]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/modules/access/vcdx'
make[5]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/modules/access/vcdx'
Making all in screen
make[5]: Entering directory `/home/tux/Downloads/vlc-1.1.11/modules/access/screen'
make  all-am
make[6]: Entering directory `/home/tux/Downloads/vlc-1.1.11/modules/access/screen'
make[6]: Nothing to be done for `all-am'.
make[6]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/modules/access/screen'
make[5]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/modules/access/screen'
Making all in bd
make[5]: Entering directory `/home/tux/Downloads/vlc-1.1.11/modules/access/bd'
make  all-am
make[6]: Entering directory `/home/tux/Downloads/vlc-1.1.11/modules/access/bd'
  CC     libaccess_bd_plugin_la-bd.lo
  CC     libaccess_bd_plugin_la-mpls.lo
  CC     libaccess_bd_plugin_la-clpi.lo
  CCLD   libaccess_bd_plugin.la
make[6]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/modules/access/bd'
make[5]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/modules/access/bd'
Making all in zip
make[5]: Entering directory `/home/tux/Downloads/vlc-1.1.11/modules/access/zip'
make  all-am
make[6]: Entering directory `/home/tux/Downloads/vlc-1.1.11/modules/access/zip'
  CC     libzip_plugin_la-zipstream.lo
zipstream.c: In function 'ZipIO_Write':
zipstream.c:842: warning: unused variable 'ERROR_zip_cannot_write_this_should_not_happen'
  CC     libzip_plugin_la-zipaccess.lo
zipaccess.c: In function 'ZipIO_Open':
zipaccess.c:369: warning: unused parameter 'mode'
zipaccess.c: In function 'ZipIO_Write':
zipaccess.c:398: warning: unused variable 'zip_access_cannot_write_this_should_not_happen'
  CCLD   libzip_plugin.la
make[6]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/modules/access/zip'
make[5]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/modules/access/zip'
make[5]: Entering directory `/home/tux/Downloads/vlc-1.1.11/modules/access'
  CC     libaccess_alsa_plugin_la-alsa.lo
  CCLD   libaccess_alsa_plugin.la
  CC     libaccess_avio_plugin_la-avio.lo
  CCLD   libaccess_avio_plugin.la
  CC     libaccess_dv_plugin_la-dv.lo
dv.c: In function 'Open':
dv.c:242: warning: ignoring return value of 'vlc_thread_create', declared with attribute warn_unused_result
  CCLD   libaccess_dv_plugin.la
  CC     libaccess_jack_plugin_la-jack.lo
jack.c: In function 'Open':
jack.c:161: warning: 'jack_client_new' is deprecated (declared at /usr/include/jack/jack.h:105)
jack.c:465:2: warning: #warning Hmm.... looks wrong
  CCLD   libaccess_jack_plugin.la
  CC     libaccess_mmap_plugin_la-mmap.lo
mmap.c: In function 'Block':
mmap.c:176: warning: comparison between signed and unsigned integer expressions
  CCLD   libaccess_mmap_plugin.la
  CC     libaccess_oss_plugin_la-oss.lo
  CCLD   libaccess_oss_plugin.la
  CC     libaccess_smb_plugin_la-smb.lo
  CCLD   libaccess_smb_plugin.la
  CC     libcdda_plugin_la-cdda.lo
  CC     libcdda_plugin_la-cdrom.lo
  CCLD   libcdda_plugin.la
  CC     libdvdnav_plugin_la-dvdnav.lo
dvdnav.c: In function 'Demux':
dvdnav.c:680: warning: call to 'harmful_delay' declared with attribute warning: use proper event handling instead of short delay
dvdnav.c:902: warning: call to 'harmful_delay' declared with attribute warning: use proper event handling instead of short delay
  CCLD   libdvdnav_plugin.la
  CC     libdvdread_plugin_la-dvdread.lo
  CCLD   libdvdread_plugin.la
  CC     libv4l2_plugin_la-v4l2.lo
v4l2.c: In function 'OpenVideoDev':
v4l2.c:1923: warning: format '%lx' expects type 'long unsigned int', but argument 5 has type 'v4l2_std_id'
  CCLD   libv4l2_plugin.la
  CC     libfilesystem_plugin_la-file.lo
  CC     libfilesystem_plugin_la-directory.lo
  CC     libfilesystem_plugin_la-fs.lo
  CCLD   libfilesystem_plugin.la
  CC     libaccess_udp_plugin_la-udp.lo
  CCLD   libaccess_udp_plugin.la
  CC     libaccess_tcp_plugin_la-tcp.lo
  CCLD   libaccess_tcp_plugin.la
  CC     libaccess_http_plugin_la-http.lo
http.c: In function 'Read':
http.c:814: warning: comparison between signed and unsigned integer expressions
http.c:837: warning: comparison between signed and unsigned integer expressions
http.c: In function 'Request':
http.c:1445: warning: comparison between signed and unsigned integer expressions
  CCLD   libaccess_http_plugin.la
  CC     libaccess_ftp_plugin_la-ftp.lo
  CCLD   libaccess_ftp_plugin.la
  CC     libaccess_fake_plugin_la-fake.lo
  CCLD   libaccess_fake_plugin.la
  CC     libaccess_imem_plugin_la-imem.lo
  CCLD   libaccess_imem_plugin.la
  CC     libaccess_attachment_plugin_la-attachment.lo
attachment.c: In function 'Read':
attachment.c:119: warning: comparison between signed and unsigned integer expressions
  CCLD   libaccess_attachment_plugin.la
  CC     libxcb_screen_plugin_la-xcb.lo
screen/xcb.c: In function 'Demux':
screen/xcb.c:329: warning: 'tc.sequence' may be used uninitialized in this function
screen/xcb.c:330: warning: 'qc.sequence' may be used uninitialized in this function
  CCLD   libxcb_screen_plugin.la
make[5]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/modules/access'
make[4]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/modules/access'
make[3]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/modules/access'
Making all in audio_filter
make[3]: Entering directory `/home/tux/Downloads/vlc-1.1.11/modules/audio_filter'
make  all-recursive
make[4]: Entering directory `/home/tux/Downloads/vlc-1.1.11/modules/audio_filter'
Making all in channel_mixer
make[5]: Entering directory `/home/tux/Downloads/vlc-1.1.11/modules/audio_filter/channel_mixer'
make  all-am
make[6]: Entering directory `/home/tux/Downloads/vlc-1.1.11/modules/audio_filter/channel_mixer'
  CC     libdolby_surround_decoder_plugin_la-dolby.lo
  CCLD   libdolby_surround_decoder_plugin.la
  CC     libheadphone_channel_mixer_plugin_la-headphone.lo
  CCLD   libheadphone_channel_mixer_plugin.la
  CC     libmono_plugin_la-mono.lo
  CCLD   libmono_plugin.la
  CC     libsimple_channel_mixer_plugin_la-simple.lo
  CCLD   libsimple_channel_mixer_plugin.la
  CC     libtrivial_channel_mixer_plugin_la-trivial.lo
  CCLD   libtrivial_channel_mixer_plugin.la
make[6]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/modules/audio_filter/channel_mixer'
make[5]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/modules/audio_filter/channel_mixer'
Making all in converter
make[5]: Entering directory `/home/tux/Downloads/vlc-1.1.11/modules/audio_filter/converter'
make  all-am
make[6]: Entering directory `/home/tux/Downloads/vlc-1.1.11/modules/audio_filter/converter'
  CC     liba52tofloat32_plugin_la-a52tofloat32.lo
  CCLD   liba52tofloat32_plugin.la
  CC     libdtstofloat32_plugin_la-dtstofloat32.lo
  CCLD   libdtstofloat32_plugin.la
  CC     libmpgatofixed32_plugin_la-mpgatofixed32.lo
  CCLD   libmpgatofixed32_plugin.la
  CC     liba52tospdif_plugin_la-a52tospdif.lo
  CCLD   liba52tospdif_plugin.la
  CC     libaudio_format_plugin_la-format.lo
  CCLD   libaudio_format_plugin.la
  CC     libconverter_fixed_plugin_la-fixed.lo
  CCLD   libconverter_fixed_plugin.la
  CC     libdtstospdif_plugin_la-dtstospdif.lo
  CCLD   libdtstospdif_plugin.la
make[6]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/modules/audio_filter/converter'
make[5]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/modules/audio_filter/converter'
Making all in resampler
make[5]: Entering directory `/home/tux/Downloads/vlc-1.1.11/modules/audio_filter/resampler'
make  all-am
make[6]: Entering directory `/home/tux/Downloads/vlc-1.1.11/modules/audio_filter/resampler'
  CC     libugly_resampler_plugin_la-ugly.lo
  CCLD   libugly_resampler_plugin.la
make[6]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/modules/audio_filter/resampler'
make[5]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/modules/audio_filter/resampler'
Making all in spatializer
make[5]: Entering directory `/home/tux/Downloads/vlc-1.1.11/modules/audio_filter/spatializer'
make  all-am
make[6]: Entering directory `/home/tux/Downloads/vlc-1.1.11/modules/audio_filter/spatializer'
  CXX    libspatializer_plugin_la-spatializer.lo
  CXX    libspatializer_plugin_la-allpass.lo
  CXX    libspatializer_plugin_la-comb.lo
  CC     libspatializer_plugin_la-denormals.lo
  CXX    libspatializer_plugin_la-revmodel.lo
  CXXLD  libspatializer_plugin.la
make[6]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/modules/audio_filter/spatializer'
make[5]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/modules/audio_filter/spatializer'
make[5]: Entering directory `/home/tux/Downloads/vlc-1.1.11/modules/audio_filter'
  CC     libaudiobargraph_a_plugin_la-audiobargraph_a.lo
  CCLD   libaudiobargraph_a_plugin.la
  CC     libchorus_flanger_plugin_la-chorus_flanger.lo
  CCLD   libchorus_flanger_plugin.la
  CC     libequalizer_plugin_la-equalizer.lo
  CCLD   libequalizer_plugin.la
  CC     libnormvol_plugin_la-normvol.lo
  CCLD   libnormvol_plugin.la
  CC     libparam_eq_plugin_la-param_eq.lo
  CCLD   libparam_eq_plugin.la
  CC     libscaletempo_plugin_la-scaletempo.lo
  CCLD   libscaletempo_plugin.la
make[5]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/modules/audio_filter'
make[4]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/modules/audio_filter'
make[3]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/modules/audio_filter'
Making all in audio_mixer
make[3]: Entering directory `/home/tux/Downloads/vlc-1.1.11/modules/audio_mixer'
make  all-am
make[4]: Entering directory `/home/tux/Downloads/vlc-1.1.11/modules/audio_mixer'
  CC     libfloat32_mixer_plugin_la-float32.lo
float32.c: In function 'Create':
float32.c:69: warning: comparison between signed and unsigned integer expressions
float32.c:74: warning: comparison between signed and unsigned integer expressions
  CCLD   libfloat32_mixer_plugin.la
  CC     libspdif_mixer_plugin_la-spdif.lo
  CCLD   libspdif_mixer_plugin.la
  CC     libtrivial_mixer_plugin_la-trivial.lo
  CCLD   libtrivial_mixer_plugin.la
make[4]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/modules/audio_mixer'
make[3]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/modules/audio_mixer'
Making all in audio_output
make[3]: Entering directory `/home/tux/Downloads/vlc-1.1.11/modules/audio_output'
make  all-am
make[4]: Entering directory `/home/tux/Downloads/vlc-1.1.11/modules/audio_output'
  CC     libalsa_plugin_la-alsa.lo
alsa.c: In function 'Probe':
alsa.c:211: warning: assignment discards qualifiers from pointer target type
alsa.c:287:3: warning: #warning Please update alsa-lib to version > 1.0.23.
alsa.c: In function 'Open':
alsa.c:660: warning: 'snd_pcm_sw_params_set_sleep_min' is deprecated (declared at /usr/include/alsa/pcm.h:1116)
alsa.c: In function 'ALSAFill':
alsa.c:902: warning: call to 'harmful_delay' declared with attribute warning: use proper event handling instead of short delay
alsa.c:798: warning: variable 'canc' might be clobbered by 'longjmp' or 'vfork'
alsa.c: In function 'Open':
alsa.c:493: warning: call to 'harmful_delay' declared with attribute warning: use proper event handling instead of short delay
  CCLD   libalsa_plugin.la
  CC     libaout_sdl_plugin_la-sdl.lo
  CCLD   libaout_sdl_plugin.la
  CC     libjack_plugin_la-jack.lo
  CCLD   libjack_plugin.la
  CC     liboss_plugin_la-oss.lo
oss.c: In function 'OSSThread':
oss.c:651: warning: call to 'harmful_delay' declared with attribute warning: use proper event handling instead of short delay
  CCLD   liboss_plugin.la
  CC     libpulse_plugin_la-pulse.lo
  CCLD   libpulse_plugin.la
  CC     libaout_file_plugin_la-file.lo
  CCLD   libaout_file_plugin.la
make[4]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/modules/audio_output'
make[3]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/modules/audio_output'
Making all in codec
make[3]: Entering directory `/home/tux/Downloads/vlc-1.1.11/modules/codec'
make  all-recursive
make[4]: Entering directory `/home/tux/Downloads/vlc-1.1.11/modules/codec'
Making all in dmo
make[5]: Entering directory `/home/tux/Downloads/vlc-1.1.11/modules/codec/dmo'
make  all-am
make[6]: Entering directory `/home/tux/Downloads/vlc-1.1.11/modules/codec/dmo'
make[6]: Nothing to be done for `all-am'.
make[6]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/modules/codec/dmo'
make[5]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/modules/codec/dmo'
Making all in avcodec
make[5]: Entering directory `/home/tux/Downloads/vlc-1.1.11/modules/codec/avcodec'
make  all-am
make[6]: Entering directory `/home/tux/Downloads/vlc-1.1.11/modules/codec/avcodec'
  CC     libavcodec_plugin_la-avcodec.lo
avcodec.c:54:5: warning: #warning You should update libavcodec to get subtitle support
avcodec.c: In function 'OpenDecoder':
avcodec.c:269: error: 'FF_MM_MMX2' undeclared (first use in this function)
avcodec.c:269: error: (Each undeclared identifier is reported only once
avcodec.c:269: error: for each function it appears in.)
avcodec.c:293: error: 'FF_MM_SSE4' undeclared (first use in this function)
avcodec.c:297: error: 'FF_MM_SSE42' undeclared (first use in this function)
make[6]: *** [libavcodec_plugin_la-avcodec.lo] Error 1
make[6]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/modules/codec/avcodec'
make[5]: *** [all] Error 2
make[5]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/modules/codec/avcodec'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/modules/codec'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/modules/codec'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/tux/Downloads/vlc-1.1.11/modules'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tux/Downloads/vlc-1.1.11'
make: *** [all] Error 2
```

I did this before under Natty but I am stuck this time.

Need some guidance at this point.

---

### Post by linuxyogi on 2011-07-26
Compiled & installed FFmpeg from source now make prints


```
LUAC   lua/extensions/allocine-fr.luac
/usr/bin/luac: lua/extensions/allocine-fr.lua:215: unexpected symbol near `#'
make[2]: *** [lua/extensions/allocine-fr.luac] Error 1
```

---

### Post by uRock on 2011-07-26
I would've used the PPA [https://launchpad.net/~n-muench/+archive/vlc](https://launchpad.net/~n-muench/+archive/vlc) The directions are on the linked page.

---

### Post by turtle153 on 2011-07-26
> **uRock said:**
> I would've used the PPA [https://launchpad.net/~n-muench/+archive/vlc](https://launchpad.net/~n-muench/+archive/vlc) The directions are on the linked page.

That said, VLC recommends you use a manual install on 10.04:
[http://www.videolan.org/vlc/download-ubuntu.html]("http://www.videolan.org/vlc/download-ubuntu.html")

---

### Post by linuxyogi on 2011-07-26
Fixed that error by installing lua5.1

I can start vlc now from the folder ./vlc but when I install it I get 

```
error while loading shared libraries: libvlc.so.5
```

Then followed [http://www.webupd8.org/2010/01/how-to-compile-vlc-and-vlmc-from-git-in.html](http://www.webupd8.org/2010/01/how-to-compile-vlc-and-vlmc-from-git-in.html)

> To fix this, you need to create symbolic links from some files in  /usr/local/lib/ in /usr/lib/. To do this, run the following command:
sudo ln -s /usr/local/lib/libvlc* /usr/lib/ sudo ln -s /usr/local/lib/libx264.a /usr/lib/ sudo ln -s /usr/local/lib/vlc /usr/lib/vlc

After applying that workaround :

```
$ vlc
VLC media player 1.1.11 The Luggage (revision exported)
[0xe29ec0] main playlist error: option playlist-autostart does not exist
[0xe26e60] main interface error: no suitable interface module
[0xe26e60] main interface error: no suitable interface module
[0xe26e60] main interface error: no suitable interface module
[0xdfa890] main libvlc error: interface "signals" initialization failed
[0xe26e60] main interface error: no suitable interface module
[0xdfa890] main libvlc error: interface "globalhotkeys,none" initialization failed
[0xdfa890] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0xe276f0] main interface error: no suitable interface module
[0xdfa890] main libvlc error: interface "default" initialization failed

```


I am ATM just running VLC from the folder.

---

### Post by linuxyogi on 2011-07-26
> **uRock said:**
> I would've used the PPA [https://launchpad.net/~n-muench/+archive/vlc]("https://launchpad.net/%7En-muench/+archive/vlc") The directions are on the linked page.

I never add PPAs unless they are mentioned at the app's official page. Please don't take this in a wrong way.

I am presently using the PPAs for wine ppa (winehq), Deluge, Pidgin. 

I really hope Vlc creates a PPA  for Ubuntu 10.04 + with the latest versions.

---

### Post by linuxyogi on 2011-07-31
```
sudo add-apt-repository ppa:lucid-bleed/ppa
sudo apt-get update  
sudo apt-get install vlc vlc-plugin-pulse mozilla-plugin-vlc
```Using the above PPA. I didnt know that it holds the latest ver. "lucid-bleed" < missed that.

[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

---

### Post by matthewlawson4916 on 2011-12-24
To get rid of the avcodec error
```

avcodec.c: In function 'OpenDecoder':
avcodec.c:269: error: 'FF_MM_MMX2' undeclared (first use in this function)
avcodec.c:269: error: (Each undeclared identifier is reported only once
avcodec.c:269: error: for each function it appears in.)
avcodec.c:293: error: 'FF_MM_SSE4' undeclared (first use in this function)
avcodec.c:297: error: 'FF_MM_SSE42' undeclared (first use in this function)
```
I changed in modules/codec/avcodec/avcodec.h
```
#   define AV_CPU_FLAG_MMX2        FF_MM_MMX2
```
to
```
#   define AV_CPU_FLAG_MMX2        FF_MM_MMXEXT
```
and commented out
```

#   define AV_CPU_FLAG_SSE4        FF_MM_SSE4
#   define AV_CPU_FLAG_SSE42       FF_MM_SSE42
```

You also need lua5.1.

---

