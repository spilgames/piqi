test: init test_cc test_compile


init:
	piqi cc -o piqi.piqi


test_cc:
	piqi cc > p.piqi
	piqi cc -o p1.piqi p.piqi
	cmp p.piqi p1.piqi

	piqi cc -t piqi >/dev/null
	piqi cc -t json >/dev/null
	piqi cc -t xml >/dev/null
	piqi cc -t pb >/dev/null

	piqi cc -t piqi piqi.piqi >/dev/null
	piqi cc -t json piqi.piqi >/dev/null
	piqi cc -t xml piqi.piqi >/dev/null
	piqi cc -t pb piqi.piqi >/dev/null


test_compile:
	piqi cc -e piqi-ocaml -t pb -o self-spec.pb piqi.piqi

	piqi compile --strict --self-spec self-spec.pb piqi.piqi >p.piqi
	piqi compile --strict --self-spec self-spec.pb -t json piqi.piqi >/dev/null
	piqi compile --strict --self-spec self-spec.pb -t xml piqi.piqi >/dev/null
	piqi compile --strict --self-spec self-spec.pb -t pb piqi.piqi >/dev/null

	piqi compile --strict --self-spec self-spec.pb -e ocaml ../../src/descriptor.proto.piqi >d.piqi
	piqi compile --strict --self-spec self-spec.pb -e ocaml -t json ../../src/descriptor.proto.piqi >/dev/null
	piqi compile --strict --self-spec self-spec.pb -e ocaml -t xml ../../src/descriptor.proto.piqi >/dev/null
	piqi compile --strict --self-spec self-spec.pb -e ocaml -t pb ../../src/descriptor.proto.piqi >/dev/null


clean:
	rm -f piqi.piqi p.piqi d.piqi p1.piqi self-spec.pb

