#
# Copyright (C) 2009 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
# $Id$

include $(TOPDIR)/rules.mk

PKG_NAME:=lxappearance
PKG_VERSION:=0.2
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=@SF/lxde
PKG_MD5SUM:=28e436c13ab09af54ffc6b415407ca37
PKG_FIXUP:=libtool
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

TARGET_CFLAGS+= \
    -I$(STAGING_DIR)/usr/lib/libintl/include/ \
    -I$(STAGING_DIR)/usr/lib/libiconv/include/

TARGET_LDFLAGS+= \
	-Wl,-rpath-link=$(STAGING_DIR)/usr/lib \
	-L$(STAGING_DIR)/usr/lib/libintl/lib \
	-L$(STAGING_DIR)/usr/lib/libiconv/lib

define Package/lxappearance
  SECTION:=xorg-app
  CATEGORY:=Xorg
  SUBMENU:=app
  TITLE:=lxappearance
  DEPENDS:=+glib2 +vte +lxde-common
endef

define Package/lxappearance/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) \
		$(PKG_INSTALL_DIR)/usr/bin/lxappearance \
		$(1)/usr/bin

	$(INSTALL_DIR) $(1)/usr/share/{lxappearance,applications}
	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/lxappearance/* \
		$(1)/usr/share/lxappearance/

	$(INSTALL_DATA) \
		$(PKG_INSTALL_DIR)/usr/share/applications/* \
		$(1)/usr/share/applications
endef

$(eval $(call BuildPackage,lxappearance))