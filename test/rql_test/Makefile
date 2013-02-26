BUILD=build
SRC=src
DRIVERS=drivers

YAML_FILES=$(shell find $(SRC) -name '*.yaml')
DRIVER_FILES=$(wildcard $(DRIVERS)/*)
TEST_FILES=$(patsubst $(DRIVERS)/driver.%,$(BUILD)/test.%,$(DRIVER_FILES))

run: $(TEST_FILES)
	./test-runner run

py js rb: $(TEST_FILES)
	./test-runner run_$@

$(TEST_FILES): $(YAML_FILES) $(DRIVER_FILES) test-runner
	mkdir -p build
	./test-runner build_test_scripts

clean:
	rm -r build

.PHONY: run py js rb clean