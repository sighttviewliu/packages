#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=keyutils
PKG_VERSION:=1.6
PKG_RELEASE:=2

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.bz2
PKG_SOURCE_URL:=https://people.redhat.com/dhowells/keyutils/
PKG_HASH:=d3aef20cec0005c0fa6b4be40079885567473185b1a57b629b030e67942c7115

include $(INCLUDE_DIR)/package.mk

define Package/libkeyutils
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=Key utilities library
  URL:=https://people.redhat.com/dhowells/keyutils/
endef

define Package/keyctl
  SECTION:=utils
  CATEGORY:=Utilities
  SUBMENU:=Encryption
  TITLE:=keyctl
  DEPENDS:=+libkeyutils
endef

define Package/keyutils/description
  Key utilities
endef

define Build/Install
	make -C $(PKG_BUILD_DIR) DESTDIR=$(PKG_INSTALL_DIR) LIBDIR=/usr/lib install
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/* $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libkeyutils.{a,so*} $(1)/usr/lib/
endef

define Package/libkeyutils/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libkeyutils.so* $(1)/usr/lib/
endef

define Package/keyctl/install
	$(INSTALL_DIR) $(1)/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/bin/keyctl $(1)/bin
endef

$(eval $(call BuildPackage,libkeyutils))
$(eval $(call BuildPackage,keyctl))
