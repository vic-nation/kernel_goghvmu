How to build Mobule for Platform
- It is only for modules are needed to using Android build system.
- Please check its own install information under its folder for other module.

[Step to build]
1. Get android open source.
    : version info - Android 4.1
    ( Download site : http://source.android.com )

2. Copy module that you want to build - to original android open source
   If same module exist in android open source, you should replace it. (no overwrite)
   
  # It is possible to build all modules at once.
  
3. You should add following text in 'build\target\board\generic\BoardConfig.mk'
 - In case of 'external\bluetooth':
   BOARD_HAVE_BLUETOOTH := true
   BOARD_HAVE_BLUETOOTH_BCM := true

 - In case of 'libalsa-intf': 
   BOARD_USES_ALSA_AUDIO := true

4. You should add module name to 'PRODUCT_PACKAGES' in 'build\target\product\core.mk' as following case.
	case 1) bluetooth : 'audio.a2dp.default' to PRODUCT_PACKAGES
	case 2) e2fsprog : should add 'e2fsck' to PRODUCT_PACKAGES
	case 3) libexifa : should add 'libexifa' to PRODUCT_PACKAGES
	case 4) libjpega : should add 'libjpega' to PRODUCT_PACKAGES
	case 5) KeyUtils : should add 'libkeyutils' to PRODUCT_PACKAGES
	case 6) bcm_dut : should add 'bcm_dut' to PRODUCT_PACKAGES
        case 7) libalsa-intf : should add 'libalsa-intf' to PRODUCT_PACKAGES
                  
ex.) [build\target\product\core.mk] - add all module name for case 1 ~ 6 at once
	PRODUCT_PACKAGES += \
		e2fsck \
		libexifa \
		libjpega \
		libkeyutils \
		audio.a2dp.default \
		qcom_audio_dut \
                qcom_dut \
                libalsa-intf

5. excute build command
   ./build.sh user
