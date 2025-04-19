# zPonds <admin@shinenet.cn>

include $(TOPDIR)/rules.mk

PKG_NAME:=nezha-agent
PKG_VERSION:=0.20.5
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/nezhahq/agent.git
PKG_SOURCE_VERSION:=c0d3615941f5afcb4833770509b049439b3e2559
PKG_SOURCE_DATE:=20250413
PKG_MIRROR_HASH:=skip

include $(INCLUDE_DIR)/package.mk

define Package/$(PKG_NAME)
	SECTION:=net
	CATEGORY:=Network
	TITLE:=Nezha Agent is the client of the Nezha panel
	URL:=https://github.com/naiba/nezha/
endef


define Package/$(PKG_NAME)/description
Nezha Agent is the client of the Nezha panel
endef

GO_PKG:=github.com/nezhahq/agent
GO_PKG_BUILD_PKG:=github.com/nezhahq/agent/cmd/agent
GO_PKG_LDFLAGS:=-s -w
GO_PKG_LDFLAGS_X:=\
  main.version=$(PKG_VERSION) \
  main.arch=$(GO_ARCH)

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/golang/golang-package.mk


define Package/nezha-agent/install
	$(call GoPackage/Package/Install/Bin,$(PKG_INSTALL_DIR))
	$(INSTALL_DIR) $(1)/usr/bin/
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/agent $(1)/usr/bin/nezha-agent
endef

$(eval $(call BuildPackage,$(PKG_NAME)))
