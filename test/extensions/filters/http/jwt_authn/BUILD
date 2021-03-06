licenses(["notice"])  # Apache 2

load(
    "//bazel:envoy_build_system.bzl",
    "envoy_cc_library",
    "envoy_cc_mock",
    "envoy_package",
)
load(
    "//test/extensions:extensions_build_system.bzl",
    "envoy_extension_cc_test",
)

envoy_package()

envoy_cc_library(
    name = "test_common_lib",
    hdrs = ["test_common.h"],
)

envoy_cc_mock(
    name = "mock_lib",
    hdrs = ["mock.h"],
    deps = [
        "//source/extensions/filters/http/jwt_authn:authenticator_lib",
        "//source/extensions/filters/http/jwt_authn:verifier_lib",
        "//test/mocks/server:server_mocks",
    ],
)

envoy_extension_cc_test(
    name = "extractor_test",
    srcs = ["extractor_test.cc"],
    extension_name = "envoy.filters.http.jwt_authn",
    deps = [
        "//source/extensions/filters/http/jwt_authn:extractor_lib",
        "//test/test_common:utility_lib",
    ],
)

envoy_extension_cc_test(
    name = "filter_test",
    srcs = ["filter_test.cc"],
    extension_name = "envoy.filters.http.jwt_authn",
    deps = [
        ":mock_lib",
        "//source/extensions/filters/http/jwt_authn:filter_lib",
        "//test/mocks/server:server_mocks",
        "//test/test_common:utility_lib",
    ],
)

envoy_extension_cc_test(
    name = "filter_factory_test",
    srcs = ["filter_factory_test.cc"],
    extension_name = "envoy.filters.http.jwt_authn",
    deps = [
        "//source/extensions/filters/http/jwt_authn:config",
        "//test/extensions/filters/http/jwt_authn:test_common_lib",
        "//test/mocks/server:server_mocks",
    ],
)

envoy_extension_cc_test(
    name = "jwks_cache_test",
    srcs = ["jwks_cache_test.cc"],
    extension_name = "envoy.filters.http.jwt_authn",
    deps = [
        "//source/extensions/filters/http/common:jwks_fetcher_lib",
        "//source/extensions/filters/http/jwt_authn:jwks_cache_lib",
        "//test/extensions/filters/http/jwt_authn:test_common_lib",
        "//test/test_common:simulated_time_system_lib",
        "//test/test_common:utility_lib",
    ],
)

envoy_extension_cc_test(
    name = "authenticator_test",
    srcs = ["authenticator_test.cc"],
    extension_name = "envoy.filters.http.jwt_authn",
    deps = [
        ":mock_lib",
        "//source/extensions/filters/http/common:jwks_fetcher_lib",
        "//source/extensions/filters/http/jwt_authn:authenticator_lib",
        "//source/extensions/filters/http/jwt_authn:filter_config_interface",
        "//source/extensions/filters/http/jwt_authn:matchers_lib",
        "//test/extensions/filters/http/common:mock_lib",
        "//test/extensions/filters/http/jwt_authn:test_common_lib",
        "//test/mocks/server:server_mocks",
        "//test/test_common:utility_lib",
    ],
)

envoy_extension_cc_test(
    name = "filter_integration_test",
    srcs = ["filter_integration_test.cc"],
    extension_name = "envoy.filters.http.jwt_authn",
    deps = [
        "//source/extensions/filters/http/jwt_authn:config",
        "//test/config:utility_lib",
        "//test/extensions/filters/http/jwt_authn:test_common_lib",
        "//test/integration:http_protocol_integration_lib",
    ],
)

envoy_extension_cc_test(
    name = "matcher_test",
    srcs = ["matcher_test.cc"],
    extension_name = "envoy.filters.http.jwt_authn",
    deps = [
        ":mock_lib",
        ":test_common_lib",
        "//source/extensions/filters/http/jwt_authn:matchers_lib",
        "//test/test_common:utility_lib",
    ],
)

envoy_extension_cc_test(
    name = "group_verifier_test",
    srcs = ["group_verifier_test.cc"],
    extension_name = "envoy.filters.http.jwt_authn",
    deps = [
        ":mock_lib",
        ":test_common_lib",
        "//source/extensions/filters/http/jwt_authn:verifier_lib",
        "//test/test_common:utility_lib",
    ],
)

envoy_extension_cc_test(
    name = "verifier_test",
    srcs = [
        "all_verifier_test.cc",
        "provider_verifier_test.cc",
    ],
    extension_name = "envoy.filters.http.jwt_authn",
    deps = [
        ":mock_lib",
        ":test_common_lib",
        "//source/extensions/filters/http/jwt_authn:filter_config_interface",
        "//source/extensions/filters/http/jwt_authn:matchers_lib",
        "//test/mocks/server:server_mocks",
        "//test/test_common:utility_lib",
    ],
)
