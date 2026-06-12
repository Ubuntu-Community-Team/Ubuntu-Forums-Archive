---
title: "Ubuntu 12.04 - Blank screen when switching to virtual terminals"
date: 2012-05-23
forum: General Help
---

### Post by LawM on 2012-05-23
Hi all,

When using ctrl+alt+fn to go to the virtual terminals, I find a blank screen. The terminals work, as I can log in and do stuff blindly, like creating files. Only the graphical mode (ctrl+alt+f7) works.

During the splash session, the vts are available and readable, only when I choose a desktop environment they turn to blank. I can reproduce this with my preferred manager, cinnamon, but also with gnome and unity 2d. I also tried an old kernel (3.0.0-12-generic) with the same results.

I've been twiking around the grub, and found out that the nomodeset flag makes the vterminal appears, but all the video acceleration is gone, so I would prefer a fix instead of a workaround.

Any help will be deeply appreciated, i'm going insane =(.

Info:

Laptop: Toshiba R830
OS: Ubuntu 12.04 x86_64
Kernel: 3.2.0-24-generic #39-Ubuntu
Graphic card: Intel Sandybridge
xorg-server 2:1.11.4-0ubuntu10.1

Logs at the time of the switch:

.xsession-errors

```
(gnome-settings-daemon:1938): color-plugin-WARNING **: Done switch to new account, reload devices
(gnome-settings-daemon:1938): color-plugin-WARNING **: unable to get EDID for xrandr-LVDS1: unable to get EDID for output
```Xorg.0.log

```
[  2513.699] (II) AIGLX: Suspending AIGLX clients for VT switch
[  2515.025] (II) Open ACPI successful (/var/run/acpid.socket)
[  2515.025] (II) AIGLX: Resuming AIGLX clients after VT switch
[  2515.501] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
```kern.log

```
May 23 22:29:06 pulpo kernel: [ 3236.061227] [drm:intel_crtc_cursor_set], 
May 23 22:29:06 pulpo kernel: [ 3236.061237] [drm:intel_crtc_cursor_set], cursor off
May 23 22:29:06 pulpo kernel: [ 3236.172963] [drm:drm_crtc_helper_set_config], 
May 23 22:29:06 pulpo kernel: [ 3236.172971] [drm:drm_crtc_helper_set_config], [CRTC:3] [FB:27] #connectors=1 (x y) (0 0)
May 23 22:29:06 pulpo kernel: [ 3236.172997] [drm:drm_crtc_helper_set_config], modes are different, full mode set
May 23 22:29:06 pulpo kernel: [ 3236.173003] [drm:drm_mode_debug_printmodeline], Modeline 39:"" 0 84750 1360 1432 1568 1776 768 771 781 798 0x0 0x6
May 23 22:29:06 pulpo kernel: [ 3236.173012] [drm:drm_mode_debug_printmodeline], Modeline 26:"1366x768" 60 76220 1366 1400 1512 1624 768 769 771 780 0x8 0xa
May 23 22:29:06 pulpo kernel: [ 3236.173025] [drm:drm_crtc_helper_set_config], [CONNECTOR:5:LVDS-1] to [CRTC:3]
May 23 22:29:06 pulpo kernel: [ 3236.173031] [drm:drm_crtc_helper_set_config], attempting to set mode from userspace
May 23 22:29:06 pulpo kernel: [ 3236.173036] [drm:drm_mode_debug_printmodeline], Modeline 26:"1366x768" 60 76220 1366 1400 1512 1624 768 769 771 780 0x8 0xa
May 23 22:29:06 pulpo kernel: [ 3236.173053] [drm:drm_crtc_helper_set_mode], [CRTC:3]
May 23 22:29:06 pulpo kernel: [ 3236.228522] [drm:intel_wait_for_vblank], vblank wait timed out
May 23 22:29:06 pulpo kernel: [ 3236.228533] [drm:ironlake_disable_fbc], disabled FBC
May 23 22:29:06 pulpo kernel: [ 3236.252965] [drm:sandybridge_update_wm], FIFO watermarks For pipe A - plane 6, cursor: 6
May 23 22:29:06 pulpo kernel: [ 3236.252977] [drm:ironlake_check_srwm], watermark 1: display plane 10, fbc lines 3, cursor 6
May 23 22:29:06 pulpo kernel: [ 3236.252985] [drm:ironlake_check_srwm], watermark 2: display plane 12, fbc lines 3, cursor 6
May 23 22:29:06 pulpo kernel: [ 3236.252991] [drm:ironlake_check_srwm], watermark 3: display plane 55, fbc lines 3, cursor 6
May 23 22:29:06 pulpo kernel: [ 3236.252998] [drm:intel_update_fbc], 
May 23 22:29:06 pulpo kernel: [ 3236.253002] [drm:intel_update_fbc], fbc set to per-chip default
May 23 22:29:06 pulpo kernel: [ 3236.253007] [drm:intel_update_fbc], framebuffer not tiled or fenced, disabling compression
May 23 22:29:06 pulpo kernel: [ 3236.253175] [drm:ironlake_get_refclk], using SSC reference clock of 120 MHz
May 23 22:29:06 pulpo kernel: [ 3236.253210] [drm:intel_choose_pipe_bpp_dither], clamping display bpc (was -1) to LVDS (6)
May 23 22:29:06 pulpo kernel: [ 3236.253216] [drm:intel_choose_pipe_bpp_dither], setting pipe bpc to 8 (max display bpc 6)
May 23 22:29:06 pulpo kernel: [ 3236.253223] [drm:ironlake_crtc_mode_set], Mode for pipe 0:
May 23 22:29:06 pulpo kernel: [ 3236.253228] [drm:drm_mode_debug_printmodeline], Modeline 26:"1366x768" 60 76220 1366 1400 1512 1624 768 769 771 780 0x8 0xa
May 23 22:29:06 pulpo kernel: [ 3236.253392] [drm] Changing LVDS panel from (-hsync, +vsync) to (-hsync, -vsync)
May 23 22:29:06 pulpo kernel: [ 3236.308491] [drm:intel_wait_for_vblank], vblank wait timed out
May 23 22:29:06 pulpo kernel: [ 3236.308514] [drm:ironlake_update_plane], Writing base 00064000 00000000 0 0 5504
May 23 22:29:06 pulpo kernel: [ 3236.308523] [drm:intel_update_fbc], 
May 23 22:29:06 pulpo kernel: [ 3236.308527] [drm:intel_update_fbc], fbc set to per-chip default
May 23 22:29:06 pulpo kernel: [ 3236.308532] [drm:intel_update_fbc], framebuffer not tiled or fenced, disabling compression
May 23 22:29:06 pulpo kernel: [ 3236.364418] [drm:intel_wait_for_vblank], vblank wait timed out
May 23 22:29:06 pulpo kernel: [ 3236.364432] [drm:sandybridge_update_wm], FIFO watermarks For pipe A - plane 6, cursor: 6
May 23 22:29:06 pulpo kernel: [ 3236.364440] [drm:ironlake_check_srwm], watermark 1: display plane 10, fbc lines 3, cursor 6
May 23 22:29:06 pulpo kernel: [ 3236.364448] [drm:ironlake_check_srwm], watermark 2: display plane 12, fbc lines 3, cursor 6
May 23 22:29:06 pulpo kernel: [ 3236.364454] [drm:ironlake_check_srwm], watermark 3: display plane 55, fbc lines 3, cursor 6
May 23 22:29:06 pulpo kernel: [ 3236.364464] [drm:drm_crtc_helper_set_mode], [ENCODER:6:LVDS-6] set [MODE:26:1366x768]
May 23 22:29:06 pulpo kernel: [ 3236.364473] [drm:sandybridge_update_wm], FIFO watermarks For pipe A - plane 6, cursor: 6
May 23 22:29:06 pulpo kernel: [ 3236.364479] [drm:ironlake_check_srwm], watermark 1: display plane 10, fbc lines 3, cursor 6
May 23 22:29:06 pulpo kernel: [ 3236.364486] [drm:ironlake_check_srwm], watermark 2: display plane 12, fbc lines 3, cursor 6
May 23 22:29:06 pulpo kernel: [ 3236.364492] [drm:ironlake_check_srwm], watermark 3: display plane 55, fbc lines 3, cursor 6
May 23 22:29:06 pulpo kernel: [ 3236.420368] [drm:intel_wait_for_vblank], vblank wait timed out
May 23 22:29:06 pulpo kernel: [ 3236.476264] [drm:intel_wait_for_vblank], vblank wait timed out
May 23 22:29:06 pulpo kernel: [ 3236.477080] [drm:gen6_fdi_link_train], FDI_RX_IIR 0x100
May 23 22:29:06 pulpo kernel: [ 3236.477086] [drm:gen6_fdi_link_train], FDI train 1 done.
May 23 22:29:06 pulpo kernel: [ 3236.477739] [drm:gen6_fdi_link_train], FDI_RX_IIR 0x600
May 23 22:29:06 pulpo kernel: [ 3236.477744] [drm:gen6_fdi_link_train], FDI train 2 done.
May 23 22:29:06 pulpo kernel: [ 3236.477748] [drm:gen6_fdi_link_train], FDI train done.
May 23 22:29:06 pulpo kernel: [ 3236.478962] [drm:intel_update_fbc], 
May 23 22:29:06 pulpo kernel: [ 3236.478966] [drm:intel_update_fbc], fbc set to per-chip default
May 23 22:29:06 pulpo kernel: [ 3236.478970] [drm:intel_update_fbc], framebuffer not tiled or fenced, disabling compression
May 23 22:29:06 pulpo kernel: [ 3236.478989] [drm:drm_crtc_helper_set_config], Setting connector DPMS state to on
May 23 22:29:06 pulpo kernel: [ 3236.478996] [drm:drm_crtc_helper_set_config],     [CONNECTOR:5:LVDS-1] set DPMS on
May 23 22:29:06 pulpo kernel: [ 3236.479031] [drm:drm_crtc_helper_set_config], 
May 23 22:29:06 pulpo kernel: [ 3236.479035] [drm:drm_crtc_helper_set_config], [CRTC:4] [NOFB]
May 23 22:29:06 pulpo kernel: [ 3236.479062] [drm:drm_crtc_helper_set_config], 
May 23 22:29:06 pulpo kernel: [ 3236.479065] [drm:drm_crtc_helper_set_config], [CRTC:3] [FB:27] #connectors=1 (x y) (0 0)
May 23 22:29:06 pulpo kernel: [ 3236.479089] [drm:drm_crtc_helper_set_config], [CONNECTOR:5:LVDS-1] to [CRTC:3]
May 23 22:29:06 pulpo kernel: [ 3236.479118] [drm:drm_crtc_helper_set_config], 
May 23 22:29:06 pulpo kernel: [ 3236.479121] [drm:drm_crtc_helper_set_config], [CRTC:3] [FB:27] #connectors=1 (x y) (0 0)
May 23 22:29:06 pulpo kernel: [ 3236.479134] [drm:drm_crtc_helper_set_config], [CONNECTOR:5:LVDS-1] to [CRTC:3]
May 23 22:29:08 pulpo kernel: [ 3237.819256] [drm:drm_mode_setcrtc], [CRTC:3]
May 23 22:29:08 pulpo kernel: [ 3237.819276] [drm:drm_mode_setcrtc], [CONNECTOR:5:LVDS-1]
May 23 22:29:08 pulpo kernel: [ 3237.819287] [drm:drm_crtc_helper_set_config], 
May 23 22:29:08 pulpo kernel: [ 3237.819293] [drm:drm_crtc_helper_set_config], [CRTC:3] [FB:34] #connectors=1 (x y) (0 0)
May 23 22:29:08 pulpo kernel: [ 3237.819326] [drm:drm_crtc_helper_set_config], modes are different, full mode set
May 23 22:29:08 pulpo kernel: [ 3237.819335] [drm:drm_mode_debug_printmodeline], Modeline 26:"1366x768" 60 76220 1366 1400 1512 1624 768 769 771 780 0x8 0xa
May 23 22:29:08 pulpo kernel: [ 3237.819351] [drm:drm_mode_debug_printmodeline], Modeline 40:"" 0 84750 1360 1432 1568 1776 768 771 781 798 0x0 0x6
May 23 22:29:08 pulpo kernel: [ 3237.819381] [drm:drm_crtc_helper_set_config], [CONNECTOR:5:LVDS-1] to [CRTC:3]
May 23 22:29:08 pulpo kernel: [ 3237.819384] [drm:drm_crtc_helper_set_config], attempting to set mode from userspace
May 23 22:29:08 pulpo kernel: [ 3237.819387] [drm:drm_mode_debug_printmodeline], Modeline 40:"" 0 84750 1360 1432 1568 1776 768 771 781 798 0x0 0x6
May 23 22:29:08 pulpo kernel: [ 3237.819395] [drm:drm_crtc_helper_set_mode], [CRTC:3]
May 23 22:29:08 pulpo kernel: [ 3237.874728] [drm:intel_wait_for_vblank], vblank wait timed out
May 23 22:29:08 pulpo kernel: [ 3237.899068] [drm:sandybridge_update_wm], FIFO watermarks For pipe A - plane 6, cursor: 6
May 23 22:29:08 pulpo kernel: [ 3237.899081] [drm:ironlake_check_srwm], watermark 1: display plane 10, fbc lines 3, cursor 6
May 23 22:29:08 pulpo kernel: [ 3237.899091] [drm:ironlake_check_srwm], watermark 2: display plane 13, fbc lines 3, cursor 6
May 23 22:29:08 pulpo kernel: [ 3237.899099] [drm:ironlake_check_srwm], watermark 3: display plane 61, fbc lines 3, cursor 6
May 23 22:29:08 pulpo kernel: [ 3237.899106] [drm:intel_update_fbc], 
May 23 22:29:08 pulpo kernel: [ 3237.899112] [drm:intel_update_fbc], fbc set to per-chip default
May 23 22:29:08 pulpo kernel: [ 3237.899120] [drm:intel_enable_fbc], scheduling delayed FBC enable
May 23 22:29:08 pulpo kernel: [ 3237.899289] [drm:ironlake_get_refclk], using SSC reference clock of 120 MHz
May 23 22:29:08 pulpo kernel: [ 3237.899326] [drm:intel_choose_pipe_bpp_dither], clamping display bpc (was -1) to LVDS (6)
May 23 22:29:08 pulpo kernel: [ 3237.899333] [drm:intel_choose_pipe_bpp_dither], setting pipe bpc to 8 (max display bpc 6)
May 23 22:29:08 pulpo kernel: [ 3237.899342] [drm:ironlake_crtc_mode_set], Mode for pipe 0:
May 23 22:29:08 pulpo kernel: [ 3237.899348] [drm:drm_mode_debug_printmodeline], Modeline 40:"" 0 84750 1360 1432 1568 1776 768 771 781 798 0x0 0x6
May 23 22:29:08 pulpo kernel: [ 3237.899512] [drm] Changing LVDS panel from (-hsync, -vsync) to (-hsync, +vsync)
r_modes], [CONNECTOR:20:HDMI-A-3] disconnected
May 23 22:29:08 pulpo kernel: [ 3238.185490] [drm:drm_mode_getconnector], [CONNECTOR:20:?]
May 23 22:29:08 pulpo kernel: [ 3238.185496] [drm:drm_helper_probe_single_connector_modes], [CONNECTOR:20:HDMI-A-3]
May 23 22:29:08 pulpo kernel: [ 3238.187786] [drm:drm_do_probe_ddc_edid], drm: skipping non-existent adapter i915 gmbus dpd
May 23 22:29:08 pulpo kernel: [ 3238.187795] [drm:drm_helper_probe_single_connector_modes], [CONNECTOR:20:HDMI-A-3] disconnected
May 23 22:29:08 pulpo kernel: [ 3238.187811] [drm:drm_mode_getconnector], [CONNECTOR:21:?]
May 23 22:29:08 pulpo kernel: [ 3238.187817] [drm:drm_helper_probe_single_connector_modes], [CONNECTOR:21:DP-2]
May 23 22:29:08 pulpo kernel: [ 3238.188330] [drm:intel_dp_aux_ch], dp_aux_ch timeout status 0x5143003e
May 23 22:29:08 pulpo kernel: [ 3238.194864] [drm:intel_dp_aux_ch], dp_aux_ch timeout status 0x5143003e
May 23 22:29:08 pulpo kernel: [ 3238.202899] [drm:intel_dp_aux_ch], dp_aux_ch timeout status 0x5143003e
May 23 22:29:08 pulpo kernel: [ 3238.210333] [drm:intel_dp_detect], DPCD: 0000000000000000
May 23 22:29:08 pulpo kernel: [ 3238.210352] [drm:drm_helper_probe_single_connector_modes], [CONNECTOR:21:DP-2] disconnected
May 23 22:29:08 pulpo kernel: [ 3238.210378] [drm:drm_mode_getconnector], [CONNECTOR:21:?]
May 23 22:29:08 pulpo kernel: [ 3238.210387] [drm:drm_helper_probe_single_connector_modes], [CONNECTOR:21:DP-2]
May 23 22:29:08 pulpo kernel: [ 3238.210900] [drm:intel_dp_aux_ch], dp_aux_ch timeout status 0x5143003e
May 23 22:29:08 pulpo kernel: [ 3238.218827] [drm:intel_dp_aux_ch], dp_aux_ch timeout status 0x5143003e
May 23 22:29:08 pulpo kernel: [ 3238.226866] [drm:intel_dp_aux_ch], dp_aux_ch timeout status 0x5143003e
May 23 22:29:08 pulpo kernel: [ 3238.234311] [drm:intel_dp_detect], DPCD: 0000000000000000
May 23 22:29:08 pulpo kernel: [ 3238.234329] [drm:drm_helper_probe_single_connector_modes], [CONNECTOR:21:DP-2] disconnected
May 23 22:29:08 pulpo kernel: [ 3238.234374] [drm:drm_mode_getconnector], [CONNECTOR:23:?]
May 23 22:29:08 pulpo kernel: [ 3238.234383] [drm:drm_helper_probe_single_connector_modes], [CONNECTOR:23:DP-3]
May 23 22:29:08 pulpo kernel: [ 3238.234897] [drm:intel_dp_aux_ch], dp_aux_ch timeout status 0x5143003e
May 23 22:29:08 pulpo kernel: [ 3238.242803] [drm:intel_dp_aux_ch], dp_aux_ch timeout status 0x5143003e
May 23 22:29:08 pulpo kernel: [ 3238.250860] [drm:intel_dp_aux_ch], dp_aux_ch timeout status 0x5143003e
May 23 22:29:08 pulpo kernel: [ 3238.258279] [drm:intel_dp_detect], DPCD: 0000000000000000
May 23 22:29:08 pulpo kernel: [ 3238.258296] [drm:drm_helper_probe_single_connector_modes], [CONNECTOR:23:DP-3] disconnected
May 23 22:29:08 pulpo kernel: [ 3238.258323] [drm:drm_mode_getconnector], [CONNECTOR:23:?]
May 23 22:29:08 pulpo kernel: [ 3238.258332] [drm:drm_helper_probe_single_connector_modes], [CONNECTOR:23:DP-3]
May 23 22:29:08 pulpo kernel: [ 3238.258849] [drm:intel_dp_aux_ch], dp_aux_ch timeout status 0x5143003e
May 23 22:29:08 pulpo kernel: [ 3238.266785] [drm:intel_dp_aux_ch], dp_aux_ch timeout status 0x5143003e
May 23 22:29:08 pulpo kernel: [ 3238.274834] [drm:intel_dp_aux_ch], dp_aux_ch timeout status 0x5143003e
May 23 22:29:08 pulpo kernel: [ 3238.282248] [drm:intel_dp_detect], DPCD: 0000000000000000
May 23 22:29:08 pulpo kernel: [ 3238.282266] [drm:drm_helper_probe_single_connector_modes], [CONNECTOR:23:DP-3] disconnected
May 23 22:29:08 pulpo kernel: [ 3238.286445] [drm:intel_crtc_cursor_set], 
May 23 22:29:08 pulpo kernel: [ 3237.950789] [drm:ironlake_enable_fbc], enabled fbc on plane 0
May 23 22:29:08 pulpo kernel: [ 3237.954638] [drm:intel_wait_for_vblank], vblank wait timed out
May 23 22:29:08 pulpo kernel: [ 3237.954917] [drm:ironlake_update_plane], Writing base 01F84000 00000000 0 0 5632
May 23 22:29:08 pulpo kernel: [ 3237.954929] [drm:intel_update_fbc], 
May 23 22:29:08 pulpo kernel: [ 3237.954934] [drm:intel_update_fbc], fbc set to per-chip default
May 23 22:29:08 pulpo kernel: [ 3238.010614] [drm:intel_wait_for_vblank], vblank wait timed out
May 23 22:29:08 pulpo kernel: [ 3238.010632] [drm:sandybridge_update_wm], FIFO watermarks For pipe A - plane 6, cursor: 6
May 23 22:29:08 pulpo kernel: [ 3238.010642] [drm:ironlake_check_srwm], watermark 1: display plane 10, fbc lines 3, cursor 6
May 23 22:29:08 pulpo kernel: [ 3238.010652] [drm:ironlake_check_srwm], watermark 2: display plane 13, fbc lines 3, cursor 6
May 23 22:29:08 pulpo kernel: [ 3238.010661] [drm:ironlake_check_srwm], watermark 3: display plane 61, fbc lines 3, cursor 6
May 23 22:29:08 pulpo kernel: [ 3238.010674] [drm:drm_crtc_helper_set_mode], [ENCODER:6:LVDS-6] set [MODE:40:]
May 23 22:29:08 pulpo kernel: [ 3238.010685] [drm:sandybridge_update_wm], FIFO watermarks For pipe A - plane 6, cursor: 6
May 23 22:29:08 pulpo kernel: [ 3238.010693] [drm:ironlake_check_srwm], watermark 1: display plane 10, fbc lines 3, cursor 6
May 23 22:29:08 pulpo kernel: [ 3238.010803] [drm:ironlake_check_srwm], watermark 2: display plane 13, fbc lines 3, cursor 6
May 23 22:29:08 pulpo kernel: [ 3238.010813] [drm:ironlake_check_srwm], watermark 3: display plane 61, fbc lines 3, cursor 6
May 23 22:29:08 pulpo kernel: [ 3238.066551] [drm:intel_wait_for_vblank], vblank wait timed out
May 23 22:29:08 pulpo kernel: [ 3238.122428] [drm:intel_wait_for_vblank], vblank wait timed out
May 23 22:29:08 pulpo kernel: [ 3238.123245] [drm:gen6_fdi_link_train], FDI_RX_IIR 0x100
May 23 22:29:08 pulpo kernel: [ 3238.123253] [drm:gen6_fdi_link_train], FDI train 1 done.
May 23 22:29:08 pulpo kernel: [ 3238.123907] [drm:gen6_fdi_link_train], FDI_RX_IIR 0x600
May 23 22:29:08 pulpo kernel: [ 3238.123913] [drm:gen6_fdi_link_train], FDI train 2 done.
May 23 22:29:08 pulpo kernel: [ 3238.123918] [drm:gen6_fdi_link_train], FDI train done.
May 23 22:29:08 pulpo kernel: [ 3238.125134] [drm:intel_update_fbc], 
May 23 22:29:08 pulpo kernel: [ 3238.125139] [drm:intel_update_fbc], fbc set to per-chip default
May 23 22:29:08 pulpo kernel: [ 3238.125158] [drm:drm_crtc_helper_set_config], Setting connector DPMS state to on
May 23 22:29:08 pulpo kernel: [ 3238.125166] [drm:drm_crtc_helper_set_config],     [CONNECTOR:5:LVDS-1] set DPMS on
May 23 22:29:08 pulpo kernel: [ 3238.125368] [drm:drm_mode_getconnector], [CONNECTOR:5:?]
May 23 22:29:08 pulpo kernel: [ 3238.125375] [drm:drm_helper_probe_single_connector_modes], [CONNECTOR:5:LVDS-1]
May 23 22:29:08 pulpo kernel: [ 3238.125397] [drm:drm_helper_probe_single_connector_modes], [CONNECTOR:5:LVDS-1] probed modes :
May 23 22:29:08 pulpo kernel: [ 3238.125405] [drm:drm_mode_debug_printmodeline], Modeline 25:"1366x768" 60 76220 1366 1400 1512 1624 768 769 771 780 0x8 0xa
May 23 22:29:08 pulpo kernel: [ 3238.125419] [drm:drm_mode_getconnector], [CONNECTOR:5:?]
May 23 22:29:08 pulpo kernel: [ 3238.125733] [drm:drm_mode_getconnector], [CONNECTOR:9:?]
May 23 22:29:08 pulpo kernel: [ 3238.125740] [drm:drm_helper_probe_single_connector_modes], [CONNECTOR:9:VGA-1]
May 23 22:29:08 pulpo kernel: [ 3238.125749] [drm:intel_ironlake_crt_detect_hotplug], ironlake hotplug adpa=0xf40000, result 0
May 23 22:29:08 pulpo kernel: [ 3238.125756] [drm:intel_crt_detect], CRT not detected via hotplug
May 23 22:29:08 pulpo kernel: [ 3238.125762] [drm:drm_helper_probe_single_connector_modes], [CONNECTOR:9:VGA-1] disconnected
May 23 22:29:08 pulpo kernel: [ 3238.125771] [drm:drm_mode_getconnector], [CONNECTOR:9:?]
May 23 22:29:08 pulpo kernel: [ 3238.125776] [drm:drm_helper_probe_single_connector_modes], [CONNECTOR:9:VGA-1]
May 23 22:29:08 pulpo kernel: [ 3238.125783] [drm:intel_ironlake_crt_detect_hotplug], ironlake hotplug adpa=0xf40000, result 0
May 23 22:29:08 pulpo kernel: [ 3238.125790] [drm:intel_crt_detect], CRT not detected via hotplug
May 23 22:29:08 pulpo kernel: [ 3238.125796] [drm:drm_helper_probe_single_connector_modes], [CONNECTOR:9:VGA-1] disconnected
May 23 22:29:08 pulpo kernel: [ 3238.125807] [drm:drm_mode_getconnector], [CONNECTOR:12:?]
May 23 22:29:08 pulpo kernel: [ 3238.125813] [drm:drm_helper_probe_single_connector_modes], [CONNECTOR:12:HDMI-A-1]
May 23 22:29:08 pulpo kernel: [ 3238.128123] [drm:drm_do_probe_ddc_edid], drm: skipping non-existent adapter i915 gmbus dpb
May 23 22:29:08 pulpo kernel: [ 3238.128133] [drm:drm_helper_probe_single_connector_modes], [CONNECTOR:12:HDMI-A-1] disconnected
May 23 22:29:08 pulpo kernel: [ 3238.128144] [drm:drm_mode_getconnector], [CONNECTOR:12:?]
May 23 22:29:08 pulpo kernel: [ 3238.128150] [drm:drm_helper_probe_single_connector_modes], [CONNECTOR:12:HDMI-A-1]
May 23 22:29:08 pulpo kernel: [ 3238.130434] [drm:drm_do_probe_ddc_edid], drm: skipping non-existent adapter i915 gmbus dpb
May 23 22:29:08 pulpo kernel: [ 3238.130442] [drm:drm_helper_probe_single_connector_modes], [CONNECTOR:12:HDMI-A-1] disconnected
May 23 22:29:08 pulpo kernel: [ 3238.130473] [drm:drm_mode_getconnector], [CONNECTOR:15:?]
May 23 22:29:08 pulpo kernel: [ 3238.130480] [drm:drm_helper_probe_single_connector_modes], [CONNECTOR:15:DP-1]
May 23 22:29:08 pulpo kernel: [ 3238.130994] [drm:intel_dp_aux_ch], dp_aux_ch timeout status 0x5143003e
May 23 22:29:08 pulpo kernel: [ 3238.138923] [drm:intel_dp_aux_ch], dp_aux_ch timeout status 0x5143003e
May 23 22:29:08 pulpo kernel: [ 3238.146904] [drm:intel_dp_aux_ch], dp_aux_ch timeout status 0x5143003e
May 23 22:29:08 pulpo kernel: [ 3238.154441] [drm:intel_dp_detect], DPCD: 0000000000000000
May 23 22:29:08 pulpo kernel: [ 3238.154458] [drm:drm_helper_probe_single_connector_modes], [CONNECTOR:15:DP-1] disconnected
May 23 22:29:08 pulpo kernel: [ 3238.154484] [drm:drm_mode_getconnector], [CONNECTOR:15:?]
May 23 22:29:08 pulpo kernel: [ 3238.154492] [drm:drm_helper_probe_single_connector_modes], [CONNECTOR:15:DP-1]
May 23 22:29:08 pulpo kernel: [ 3238.155006] [drm:intel_dp_aux_ch], dp_aux_ch timeout status 0x5143003e
May 23 22:29:08 pulpo kernel: [ 3238.162900] [drm:intel_dp_aux_ch], dp_aux_ch timeout status 0x5143003e
May 23 22:29:08 pulpo kernel: [ 3238.170893] [drm:intel_dp_aux_ch], dp_aux_ch timeout status 0x5143003e
May 23 22:29:08 pulpo kernel: [ 3238.178433] [drm:intel_dp_detect], DPCD: 0000000000000000
May 23 22:29:08 pulpo kernel: [ 3238.178450] [drm:drm_helper_probe_single_connector_modes], [CONNECTOR:15:DP-1] disconnected
May 23 22:29:08 pulpo kernel: [ 3238.178495] [drm:drm_mode_getconnector], [CONNECTOR:18:?]
May 23 22:29:08 pulpo kernel: [ 3238.178504] [drm:drm_helper_probe_single_connector_modes], [CONNECTOR:18:HDMI-A-2]
May 23 22:29:08 pulpo kernel: [ 3238.180803] [drm:drm_do_probe_ddc_edid], drm: skipping non-existent adapter i915 gmbus dpc
May 23 22:29:08 pulpo kernel: [ 3238.180811] [drm:drm_helper_probe_single_connector_modes], [CONNECTOR:18:HDMI-A-2] disconnected
May 23 22:29:08 pulpo kernel: [ 3238.180820] [drm:drm_mode_getconnector], [CONNECTOR:18:?]
May 23 22:29:08 pulpo kernel: [ 3238.180826] [drm:drm_helper_probe_single_connector_modes], [CONNECTOR:18:HDMI-A-2]
May 23 22:29:08 pulpo kernel: [ 3238.183158] [drm:drm_do_probe_ddc_edid], drm: skipping non-existent adapter i915 gmbus dpc
May 23 22:29:08 pulpo kernel: [ 3238.183167] [drm:drm_helper_probe_single_connector_modes], [CONNECTOR:18:HDMI-A-2] disconnected
May 23 22:29:08 pulpo kernel: [ 3238.183184] [drm:drm_mode_getconnector], [CONNECTOR:20:?]
May 23 22:29:08 pulpo kernel: [ 3238.183191] [drm:drm_helper_probe_single_connector_modes], [CONNECTOR:20:HDMI-A-3]
May 23 22:29:08 pulpo kernel: [ 3238.185475] [drm:drm_do_probe_ddc_edid], drm: skipping non-existent adapter i915 gmbus dpd

```

---

### Post by LawM on 2012-05-26
Bump. Anyone? I'm going insane without my vts and considering an alternate OS. Yes, it's that bad...

---

### Post by steeldriver on 2012-05-26
can you connect an external monitor and see if the problem is the same? most often I think the issue is simply that the screen goes into an unsupported mode (wrong geometry or resolution - sometimes just the displayed text falling off the edge) - splash screen would likely use a VGA mode

there are also issues with LCD backlights not turning on but I think that's mostly on resume from suspend rather than vt switching

---

### Post by LawM on 2012-05-26
Seems like the backlight is causing issues here, specially since I can blindly use the terminals.

I like the idea of trying the external monitor, and that will be my next step, thx steeldriver.

---

### Post by LawM on 2012-05-26
Terminals! Plugging an external monitor did the trick. Of course, when I unplug it, I go back to my vtless state, any ideas how to fix it?

Here is a copy of my new Xorg.0.log:

```
[ 64461.939] (II) AIGLX: Suspending AIGLX clients for VT switch
[ 64462.913] (II) Open ACPI successful (/var/run/acpid.socket)
[ 64462.913] (II) AIGLX: Resuming AIGLX clients after VT switch
[ 64462.913] (EE) intel(0): Couldn't create pixmap for fbcon
[ 64463.092] (II) intel(0): EDID vendor "IFS", prod id 48640
[ 64463.092] (II) intel(0): Using hsync ranges from config file
[ 64463.092] (II) intel(0): Using vrefresh ranges from config file
[ 64463.092] (II) intel(0): Printing DDC gathered Modelines:
[ 64463.092] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[ 64463.092] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[ 64463.092] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[ 64463.092] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[ 64463.092] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[ 64463.092] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[ 64463.092] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[ 64463.092] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[ 64463.092] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[ 64463.092] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[ 64463.092] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[ 64463.092] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[ 64463.249] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found

```

---

### Post by LawM on 2012-05-26
After tons of google searches, I'm still unable to see my terminals without an external monitor, which kinda defeats the purpose of having a laptop...

So, my efforts:

To find the resolutions supported by my hw:

```
law@pulpo:~$ sudo hwinfo --framebuffer                               
[sudo] password for law: 
> hal.1: read hal dataprocess 2507: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 282.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.464]
  Unique ID: rdCR.ku_DuSHewh1
  Hardware Class: framebuffer
  Model: "Intel(R)Sandybridge Mobile Graphics Controller"
  Vendor: "Intel Corporation"
  Device: "Intel(R)Sandybridge Mobile Graphics Controller"
  SubVendor: "Intel(R)Sandybridge Mobile Graphics Chipset Accelerated VGA BIOS"
  SubDevice: 
  Revision: "Hardware Version 0.0"
  Memory Size: 63 MB + 960 kB
  Memory Range: 0xb0000000-0xb3feffff (rw)
  Mode 0x0360: 1280x720 (+1280), 8 bits
  Mode 0x0361: 1280x720 (+2560), 16 bits
  Mode 0x0362: 1280x720 (+5120), 24 bits
[B]  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits[/B]
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+832), 8 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```

So i did my configurations using the highlighted modes.

First, I changed my boot line to add vga=0x****. No terminals.

Following this thread, [http://ubuntuforums.org/showthread.php?t=122936&page=2](http://ubuntuforums.org/showthread.php?t=122936&page=2), I tried vga=791 instead. Still no luck.

Then I tried this one, [http://www.linuxquestions.org/questions/ubuntu-63/changing-virtual-console-screen-resolution-860061/](http://www.linuxquestions.org/questions/ubuntu-63/changing-virtual-console-screen-resolution-860061/), with my selected resolution. No changes.

I found a new thread, [http://members.home.nl/g8m/ehcs/62.html](http://members.home.nl/g8m/ehcs/62.html), maybe this one is the charmed one? Well, it isn't.

I updated my /etc/default/grub to read:
GRUB_GFXMODE=1024x768
GRUB_GFXPAYLOAD_LINUX=1024x768

Nope. Maybe if i comment out the second line? I wish...

So, any other suggestions? Am I missing something?

---

### Post by LawM on 2012-05-28
Bump! Help, please  -puppy eyes-

---

### Post by marceloguedes on 2012-06-01
Hi. I don't think is a solution but maybe it can help.
I had a very similar problem and end up discovering the issue is related to grup. What I did:

$ sudo vim /etc/default/grub 

Uncommented line:

GRUB_TERMINAL=console

It will activate the simpler console mode for grub. So:

$ sudo update-grub

Reboot and go.

I don't care about vga terminals so it fits well for me. Because it doesn't bring a high resolution terminal I guess my answer is not exactly what you want. But I expect someone else finds it useful.

---

### Post by LawM on 2012-06-03
> **marceloguedes said:**
> Hi. I don't think is a solution but maybe it can help.
I had a very similar problem and end up discovering the issue is related to grup. What I did:

$ sudo vim /etc/default/grub 

Uncommented line:

GRUB_TERMINAL=console

It will activate the simpler console mode for grub. So:

$ sudo update-grub

Reboot and go.

I don't care about vga terminals so it fits well for me. Because it doesn't bring a high resolution terminal I guess my answer is not exactly what you want. But I expect someone else finds it useful.

Unfortunately that didn't work =(.

I have an update, the vts issue is fixed with the new kernel (v3.4-precise), but it breaks virtualbox (i have to use exchange and ie for my job, so i can't do without it)... the drivers can't not be stopped/started, causing the computer to not even be able to be rebooted/shut down. Also, the usb devices stop being recognized and OpenGL crashes the computer... so, back to square 1. 

Any way to get a list of changes made to the new kernel as to detect the one causing the vts issue?

Update: 3.3.7 is a bad mix of both faulty kernels, no vbox and no vts, so I'm guessing 3.4 fixed the issue. Changelog:

> 
**2.2. Graphics**

  
[LIST]
[*]Initial drm/kms driver for the DisplayLink devices [(commit)]("http://git.kernel.org/linus/5320918b9a87865223fd6b228e530bf30bc64d9d") 
[*]exynos: added virtual display driver. This driver would be used for wireless display  [(commit)]("http://git.kernel.org/linus/") 
[*]PRIME interface to dma-buf [(commit)]("http://git.kernel.org/linus/3248877ea1796915419fba7c89315fdbf00cb56a") 
[*]Resurrect Intel740 driver: i740fb [(commit)]("http://git.kernel.org/linus/") 
[*]vmwgfx: Add page flip support [(commit)]("http://git.kernel.org/linus/") 
[*]fbdev: da8xx: add support for SP10Q010 display [(commit)]("http://git.kernel.org/linus/") 
[*]OMAPFB 

[LIST]
[*]Remove OMAP2/3 support from old omapfb driver [(commit)]("http://git.kernel.org/linus/") 
[*]Remove old blizzard driver [(commit)]("http://git.kernel.org/linus/")
[/LIST]
[/LIST]


Any pointers?

---

### Post by LawM on 2012-06-10
Bump, help?

---

### Post by LawM on 2012-06-10
OMG, i found the issue, after another weekend of google searches:

[http://www.worldofnubcraft.com/1813/black-screen-on-logout-on-ubuntu-11-10](http://www.worldofnubcraft.com/1813/black-screen-on-logout-on-ubuntu-11-10)

I'm very very disappointed on Ubuntu right now and looking for a new distro, specially after the latest update from the update manager destroyed my MBR once again.

I leave the solution here for whoever needs it.

vim ~/.config/monitors.xml
replace 1360 by 1366
save changes
open display and change to the current resolution.

Thanks to everyone who helped.

---

### Post by markskayff on 2012-09-02
Hi LawM,

Sorry you went through this but your inputs helped me to solve this same issue in my machine.

My VT were not showing when ALT+Ctrl+(F1..F6). And yes, it seems it was this resolution issue. When turn it again from 1360 to 1366 it started displying again,

Thanks to your search,

Mark.

---

### Post by Drone4four on 2013-03-25
I fiddled around with some variables in settings in /etc/default/grub.  After modifying each parameter I entered sudo update-grub.

For starters I removed the comment to activate GRUB_TERMINAL=console.  I also added the &#8216;text&#8217; parameter to the &#8216;GRUB_CMDLINE_LINUX_DEFAULT&#8217; field as per the recommendation by izx [here]("http://askubuntu.com/questions/147618/how-do-i-get-ctrlaltf-virtual-terminals-to-work-in-ubuntu-12-04?rq=1").  When I rebooted, instead of loading ldm, it gave me a CLI login.  I logged in, like the good ol&#8217; days on Slackware 9 when I was first introduced to *nix.  I entered xwmconfig, but no dice.  I entered startx to see what would happen and all I saw was my stupid wallpaper.  There was no way to load an app b/c Alt+F2 did nothing.  There was no top bar (I run gnome 3) and therefore no way to log out.  Switching back to tty1 also was impossible Ctrl+Alt+F1 through F6 did nothing.  I had no option but to do a cold reboot. 

I added "vga=normal" to my &#8216;GRUB_CMDLINE_LINUX_DEFAULT&#8217; next to "quiet splash" as per neon_overload&#8217;s post [here]("http://askubuntu.com/questions/150610/why-are-virtual-terminal-blank-using-nvidia-propietary-drivers").  

I also tried changing the vga variable from normal to 791 which also didn&#8217;t allow me to switch virtual terminals.

EDIT: One more thing, there is no ~/.config/monitors.xml for me to change the parameters for the resolution which was the case for the other posters.

Here is my /etc/default/grub

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash vga=normal"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

Here is lsmod and lspci:
```

gnull@quantal ~ $ lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     32007  4 
pci_stub               12622  1 
vboxpci                23157  0 
vboxnetadp             25670  0 
vboxnetflt             23442  0 
vboxdrv               287189  3 vboxpci,vboxnetadp,vboxnetflt
coretemp               13400  0 
kvm_intel             132759  0 
kvm                   414070  1 kvm_intel
hid_generic            12493  0 
gpio_ich               13383  0 
snd_hda_codec_realtek    77876  1 
usbhid                 46947  0 
hid                   100366  2 hid_generic,usbhid
snd_usb_audio         130279  2 
snd_usbmidi_lib        24953  1 snd_usb_audio
snd_hda_intel          33491  6 
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  2 snd_usb_audio,snd_hda_codec
snd_pcm                96580  5 snd_hda_codec_hdmi,snd_usb_audio,snd_hda_intel,snd_hda_codec
psmouse                95552  0 
microcode              22803  0 
snd_seq_midi           13324  0 
snd_rawmidi            30512  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
serio_raw              13215  0 
bnep                   18140  2 
rfcomm                 46619  0 
bluetooth             209199  10 bnep,rfcomm
parport_pc             32688  1 
ppdev                  17073  0 
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
nvidia              11300875  40 
binfmt_misc            17500  1 
mac_hid                13205  0 
snd                    78734  27 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_usb_audio,snd_usbmidi_lib,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lpc_ich                17061  0 
soundcore              15047  1 snd
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
e1000                 114778  0 
pata_jmicron           12747  0 
r8169                  61650  0 
usb_storage            48838  1 
gnull@quantal ~ $ lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:1a.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6
00:1d.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIB (ICH10) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
01:00.0 VGA compatible controller: NVIDIA Corporation GF114 [GeForce GTX 560 Ti] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GF114 HDMI Audio Controller (rev a1)
03:00.0 IDE interface: JMicron Technology Corp. JMB368 IDE controller
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
05:03.0 Ethernet controller: Intel Corporation 82541PI Gigabit Ethernet Controller (rev 05)
gnull@quantal ~ $ 

```
Here is my xorg.conf:
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 304.64  (buildmeister@swio-display-x86-rhel47-12)  Tue Oct 30 12:04:46 PDT 2012


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 81.0
    VertRefresh     50.0 - 63.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```
I don&#8217;t know how relevant my xorg.conf is b/c  i thought i read somewhere that when using nvidia&#8217;s proprietary drivers.  If this is true, then where does X11 store all of its configuration settings.

---

