android_device_sony_nypon-4.3
=============================

AOSP Omni ROM for Sony Xperia P

Getting Started :

    mkdir Omni
    cd Omni
    repo init -u git://github.com/percy-g2/android-2.git -b android-4.3
    repo sync -j16

Patch android source code :

    patch -p1 < device/sony/nypon/patches/external_bluetooth_bluedroid.patch
    patch -p1 < device/sony/nypon/patches/framework_av.patch
    patch -p1 < device/sony/nypon/patches/framework_native.patch
    patch -p1 < device/sony/nypon/patches/hardware_libhardware.patch
    patch -p1 < device/sony/nypon/patches/hardware_libhardware_legacy.patch
    patch -p1 < device/sony/nypon/patches/system_core.patch

Our step is optional!!! Use only if you going to sync Omni source code daily, than simple revert each patch before you sync CM source code :

    patch -p1 -R < device/sony/nypon/patches/external_bluetooth_bluedroid.patch
    patch -p1 -R < device/sony/nypon/patches/framework_av.patch
    patch -p1 -R < device/sony/nypon/patches/framework_native.patch
    patch -p1 -R < device/sony/nypon/patches/hardware_libhardware.patch
    patch -p1 -R < device/sony/nypon/patches/hardware_libhardware_legacy.patch
    patch -p1 -R < device/sony/nypon/patches/system_core.patch
    repo forall -p -c 'git checkout -f'
    repo sync
    patch -p1 < device/sony/nypon/patches/external_bluetooth_bluedroid.patch
    patch -p1 < device/sony/nypon/patches/framework_av.patch
    patch -p1 < device/sony/nypon/patches/framework_native.patch
    patch -p1 < device/sony/nypon/patches/hardware_libhardware.patch
    patch -p1 < device/sony/nypon/patches/hardware_libhardware_legacy.patch
    patch -p1 < device/sony/nypon/patches/system_core.patch


You are ready to build :

    . build/envsetup.sh
    lunch custom_nypon-eng
    make otapackage

ENJOY! 
